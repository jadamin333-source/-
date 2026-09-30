# 개발자 참고사항

확인일: 2026-09-05. API 구현 요청이 있을 때만 읽는다. 실제 구현 전 현재 공식 문서를 다시 확인한다.

## 연결할 때 확인할 사항

- 공식 모델 ID는 gpt-6-astra이다.
- Astra에서 도구 호출을 구현할 때는 Responses API를 사용한다.
- reasoning.effort의 지원값은 low, medium, high, xhigh, max이며 none은 지원하지 않는다.
- 사용자 지정 temperature, top_p, logprobs는 지원하지 않는다.
- 비동기 도구 호출, 작업 중 추가 지시, 대화 중 추론 강도 변경은 각각 애플리케이션 구현이 필요하다. 이 스킬을 읽는 것만으로 활성화되지 않는다.
- 이미지 입력과 이미지 생성 도구 사용을 구분한다. 사용 가능한 도구·인증·요금제는 실행 환경에서 확인한다.

근거: [모델 사양](https://developers.openai.com/api/docs/models/gpt-6-astra), [API 변경 기록](https://developers.openai.com/api/docs/changelog), [Astra 활용 가이드](https://developers.openai.com/api/docs/guides/latest-model).

## 모델 선택과 가이드 연결

자체 애플리케이션에서는 검증된 모델 설정값이 gpt-6-astra일 때 이 가이드의 실행 규칙을 요청 지침에 포함하도록 설계할 수 있다. 사용자 입력 문장에 Astra라는 단어가 있다는 이유만으로 현재 모델로 간주하지 않는다.

이 조건 연결은 애플리케이션 설계 제안이다. ChatGPT 모델 선택 메뉴의 자동 실행 기능이나 표준 스킬 이벤트 훅으로 소개하지 않는다. 이 배포본에는 자동 연결 코드나 계정 설정 변경이 포함되어 있지 않다.

API 키를 공유용 스킬에 기록하지 않는다. 실행 시 필요한 인증은 대상 환경에서 제공한다.
