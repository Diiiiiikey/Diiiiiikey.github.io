---
layouts: post
title: "[Project Refactoring]HomePage refactoring"
categories: Main-Project
tag: [codestates]
toc: true
sidebar:
  nav: "docs"
---

HomePage에는 세 개의 커스텀 훅이 사용된다

1. CommissionId로 filter된 Commissions
2. ViewCount로 filter된 Commissions
3. 랜덤 Tag로 filter된 Commissions

```js
const commissionsFilterdCommissionId = getCommissionsFn("commissionId");
const commissionsFilterdViewCount = getCommissionsFn("viewCount");
const commissionsFilterdTags = getTagsCommissionsFn();
```

기존의 getTagsCommissionsFn

```js
export const getTagsCommissionsFn = () => {
  const [tag, setTag] = useState("그림");
  const [tagsCommissions, setTagsCommissions] = useState(null);
  const [loading, setLoading] = useState(true);

  const randomNum = Math.floor(Math.random() * 10 + 1);

  useEffect(() => {
    const fetch = async () => {
      const { data, status } = await getTags();
      if (status < 300) {
        const tagName = data.data[randomNum].tagName;
        setTag(tagName);
      }
    };
    fetch();
  }, [setTag]);

  useEffect(() => {
    const fetch = async () => {
      const { data, status } = await getTagsSearch(tag);
      if (status < 300) {
        setTagsCommissions(data.data);
        setLoading(false);
      }
    };
    fetch();
  }, [setTagsCommissions, setLoading, setTag, tag]);
  return { tagsCommissions, loading };
};
```

첫번째 useEffect는 getTags로 tag 10개를 가져오고 const tagName = data.data[randomNum].tagName 으로 랜덤으로 하나의 tag를 선택한다

선택된 tag는 setTag(tagName)로 useState 에 담긴다

이때 setTag의 useState에는 디폴트로 '그림' 이 들어가 있는데 비어 놓으면 이상하게 에러가 날 때가 있었다.

순서가 어디선가 꼬일 때가 있다는 것이다.

그래서

바꾼 getTagsCommissionsFn

```js
const randomNum = Math.floor(Math.random() * 10 + 1);

export const getTagsCommissionsFn = () => {
  const [tag, setTag] = useState(null);
  const [tagsCommissions, setTagsCommissions] = useState([]);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    const fetch = async () => {
      const { data, status } = await getTags();
      if (status < 300) {
        const tagName = data.data[randomNum].tagName;
        setTag(tagName);
      }
    };
    fetch();
    const fetchTwo = async () => {
      const { data, status } = await getTagsSearch(tag);
      if (status < 300) {
        setTagsCommissions(data.data);
        setLoading(false);
      }
    };
    if (tag) {
      fetchTwo();
    }
  }, [tag, setTag, setTagsCommissions, setLoading]);
  return { tagsCommissions, loading };
};
```

우선 randomNum을 밖으로 뺐다. getTagsCommissionsFn가 여러 번 작동되는 것을 확인했고 randomNum이 바뀔 때 마다 다시 axios를 실행하게되니 가장 밖으로 빼는 선택을 했다.

그리고 useEffect를 나누는 것이 아니라 fetch 함수를 나누어서 하나의 useEffect 안에서 작동하도록 했고 실행 순서에 따라 fetch 함수를 불러왔다.

또한 첫 번째 fetch 함수로 tag를 설정하는 중에 fetchTwo 함수가 실행이되어 오류가 났다.

```
Uncaught (in promise) TypeError: Cannot destructure property 'data' of '(intermediate value)' as it is undefined. at fetchTwo (getCommissionFetch.js:54:1)
```

아마도 기존에도 이런 이유로 디폴드 state를 설정하지 않으면 오류가 났던 것 같은데 아무튼

fetchTwo를 if(tag) 안에 넣음으로써 tag가 있을 때 작동을 하게 했더니 깔끔하게 해결되었다.
