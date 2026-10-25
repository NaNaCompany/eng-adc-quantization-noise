# ADC 양자화 오차 계산기

이상적인 N비트 균일 양자화기의 전체 입력 범위에서 양자화 오차의 실효값 계산.

- ID: E142
- App: https://nanalab.kr/eng-adc-quantization-noise/
- Repository: https://github.com/NaNaCompany/eng-adc-quantization-noise
- Formula: q = V_FS/2ᴺ; e_rms = q/√12

## Model and data

입력 범위의 전체 폭을 사용합니다. 예를 들어 −1 V~+1 V는 2 V입니다. 반올림 양자화 오차가 −q/2~+q/2에 균일하고 신호와 비상관이라고 가정합니다. 과입력·DNL·INL·열잡음은 제외하며, 일정한 입력이나 동기화된 신호에서는 균일 오차 모델이 성립하지 않을 수 있습니다. 결과는 측정 ADC의 총잡음이 아닙니다.

Inputs normalize to SI. Repeated-input models support adding/removing actual input rows. Calculations, finite-number checks and physical-domain checks run locally; no external property database or solver API is used.

## Validation

Run node --test tests/*.test.mjs and python scripts/build-locales.py --check. tests/reference.json contains independently computed high-precision default and boundary references. The source notices distinguish original MIT work from citation-only external references.

## Static languages

Korean (existing root), English (`en/`), Spanish (`es/`), Simplified Chinese (`zh/`), Japanese (`ja/`) and German (`de/`). Each page has its own canonical URL, reciprocal hreflang, localized metadata, interface, validation messages and preview image. The language links work without JavaScript. Calculation code is shared and no runtime translation API is used.

Edit `localization/*.json` for text, `src/template.html` for the shared page, and run `python scripts/build-locales.py`. Run `python scripts/build-locales.py --check` and `npm test` before publishing. Decimal commas are accepted in Spanish and German; thousands separators are not supported.
