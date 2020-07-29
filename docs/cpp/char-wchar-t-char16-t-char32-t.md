---
title: char, wchar_t, char16_t, char32_t
ms.date: 02/14/2018
ms.assetid: 6b33e9f5-455b-4e49-8f12-a150cbfe2e5b
ms.openlocfilehash: 6efbae1b8f6155410b823f1abef35c3dec90d458
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232342"
---
# <a name="char-wchar_t-char16_t-char32_t"></a>char, wchar_t, char16_t, char32_t

Typy **`char`** , **`wchar_t`** **`char16_t`** i **`char32_t`** są wbudowanymi typami, które reprezentują znaki alfanumeryczne oraz symbole inne niż alfanumeryczne i znaki niedrukowalne.

## <a name="syntax"></a>Składnia

```cpp
char     ch1{ 'a' };  // or { u8'a' }
wchar_t  ch2{ L'a' };
char16_t ch3{ u'a' };
char32_t ch4{ U'a' };
```

## <a name="remarks"></a>Uwagi

**`char`** Typ to oryginalny typ znaku w C i C++. Typ **`unsigned char`** jest często używany do reprezentowania *bajtu*, który nie jest typem wbudowanym w języku C++. **`char`** Typ może służyć do przechowywania znaków z zestawu znaków ASCII lub dowolnego z zestawów znaków ISO-8859 i poszczególnych bajtów znaków wielobajtowych, takich jak Shift-JIS lub kodowanie UTF-8 zestawu znaków Unicode. Ciągi **`char`** typu są określane jako *wąskie* ciągi, nawet jeśli są używane do kodowania znaków wielobajtowych. W kompilatorze Microsoft **`char`** jest typem 8-bitowym.

**`wchar_t`** Typ jest typem szerokim zdefiniowanym dla implementacji. W kompilatorze firmy Microsoft reprezentuje 16-bitowy znak dwubajtowy używany do przechowywania kodowania Unicode zakodowanego jako UTF-16LE, natywny typ znaków w systemach operacyjnych Windows. Wersje szerokiego znaku funkcji biblioteki uniwersalnego środowiska uruchomieniowego języka C (UCRT) używają **`wchar_t`** , a jej wskaźników i typów tablic jako parametrów i zwracanych wartości, tak jak w przypadku wersji szerokiego interfejsu API systemu Windows.

**`char16_t`** Typy i **`char32_t`** reprezentują odpowiednio 16-bitowe i 32-bitowe znaki dwubajtowe. Kodowanie Unicode zakodowane jako UTF-16 może być przechowywane w **`char16_t`** typie, a kodowanie Unicode w formacie UTF-32 może być przechowywane w **`char32_t`** typie. Ciągi tych typów i **`wchar_t`** są wszystkie określane jako ciągi *szerokie* , chociaż termin często odwołuje się głównie do ciągów **`wchar_t`** typu.

W standardowej bibliotece języka C++ `basic_string` Typ jest wyspecjalizowany dla ciągów wąskich i szerokich. Użyj `std::string` , gdy znaki są typu, gdy znaki są typu, gdy znaki są typu, **`char`** `std::u16string` **`char16_t`** `std::u32string` **`char32_t`** a `std::wstring` kiedy znaki są typu **`wchar_t`** . Inne typy, które reprezentują tekst, włącznie `std::stringstream` z i `std::cout` mają specjalizacje dla ciągów wąskich i szerokich.
