---
layouts: post
title: "[Project Refactoring]FormPage"
categories: Main-Project
tag: [codestates]
toc: true
sidebar:
  nav: "docs"
---

우리는 커미션 신청을 채팅으로 하도록 설계를 했다.

하지만 정작 채팅을 구현하지 못했고 신청폼은 있으나 채팅이 없어졌으니 확인할 수 있는 방법이 없어졌다.

따라서 FormPage를 만들어야했다.

우선

getTradeFetch.js

```js
export const getTradeFn = (id) => {
  const [trades, setTrades] = useState(null);
  const [loading, setLoading] = useState(true);
  const [member, setMember] = useState(null);

  useEffect(() => {
    const fetch = async () => {
      const { data, status } = await getTrade(id);
      if (status < 300) {
        setTrades(data);
        const memberData = await getUserInfo(data.memberId);
        if (memberData.status < 300) {
          setMember(memberData.data.data);
          setLoading(false);
        }
      }
    };
    fetch();
  }, [setTrades, setMember, setLoading]);
  return { trades, member, loading };
};
```

라는 커스텀 훅을 만들었다.

원래는 getTrade만 사용해서 id로 trade의 data를 가져오도록 하기만 하면 되는데 정작 신청자의 data는 id 밖에 들어있지 않아서 다시 getUserInfo를 통해 memberId로 member의 정보를 가져와야 했다.
