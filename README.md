# Bubble Index — Community feed

Bubble Index 앱의 Community 지수만 담아 두는 공개 저장소입니다.
앱 소스는 들어 있지 않습니다.

## 어떻게 동작하나요

1. 깃허브가 매시간 `Hourly Community Index Update`를 실행합니다.
2. Adanos에서 레딧 시장 심리를 받아옵니다. API 키는 이 저장소의 Secrets에만 있습니다.
3. 결과를 `docs/community.json`에 저장합니다.
4. 앱은 아래 공개 주소를 키 없이 읽습니다.

```
https://artsidea.github.io/bubble-index-feed/community.json
```

## 점수 계산

Adanos의 감성 점수(`sentiment_score`, -1이 극단적 약세 ~ +1이 극단적 강세)를
0~100으로 펼쳐서 씁니다. 50이 중립입니다.

```
score = (sentiment_score + 1) / 2 * 100
```

`bullish_pct`와 `bearish_pct`는 Adanos가 정수로 반올림해서 내려주기 때문에
그 둘의 비율로 계산하면 값이 거의 안 움직입니다. 그래서 쓰지 않습니다.

## 키를 바꿀 때

저장소 Settings → Secrets and variables → Actions → `ADANOS_API_KEY` 값을 고치면 됩니다.
앱을 다시 올릴 필요는 없습니다.
