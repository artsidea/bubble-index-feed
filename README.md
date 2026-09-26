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

강세 의견과 약세 의견 중 강세가 차지하는 비율을 0~100으로 씁니다.
중립적인 잡담은 빼기 때문에 이야기 양이 아니라 분위기만 반영됩니다.

```
score = bullish_pct / (bullish_pct + bearish_pct) * 100
```

## 키를 바꿀 때

저장소 Settings → Secrets and variables → Actions → `ADANOS_API_KEY` 값을 고치면 됩니다.
앱을 다시 올릴 필요는 없습니다.
