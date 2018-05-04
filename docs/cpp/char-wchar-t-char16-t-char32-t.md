---
title: char, wchar_t, char16_t, char32_t | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/14/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- char_cpp
- char16_t_cpp
- wchar_t_cpp
- char32_t_cpp
dev_langs:
- C++
ms.assetid: 6b33e9f5-455b-4e49-8f12-a150cbfe2e5b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2dc38eb9742459139747578a8227bdfaee8bb8a2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="char-wchart-char16t-char32t"></a>char, wchar_t, char16_t, char32_t
Typy **char**, **wchar_t**, **char16_t** i **char32_t** są wbudowane typy, które reprezentują znaki alfanumeryczne oraz Symbole inne niż alfanumeryczne oraz znaki niedrukowalne.

## <a name="syntax"></a>Składnia

```cpp  
char     ch1{ 'a' };  // or { u8'a' }   
wchar_t  ch2{ L'a' };    
char16_t ch3{ u'a' };    
char32_t ch4{ U'a' };  
```  
  
## <a name="remarks"></a>Uwagi

**Char** typu została oryginalnego typu znaków w C i C++. Typ **unsigned char** jest często używana do reprezentowania *bajtów*, który nie jest typem wbudowanym w języku C++. **Char** typu może być używana do przechowywania znaki z zestawu znaków ASCII lub dowolne ISO 8859 zestawów znaków, a poszczególnych bajtach wielobajtowego znaki, takie jak Shift JIS lub kodowania UTF-8 zestawu znaków Unicode. Ciągi **char** typu są określane jako *zawęzić* ciągów, nawet wtedy, gdy jest używany do kodowania znaków wielobajtowego. W kompilatorze Microsoft **char** jest typem 8-bitową.

**Wchar_t** typ jest typem zdefiniowane w implementacji znaków dwubajtowych. W kompilatorze Microsoft reprezentuje 16-bitowych znaków dwubajtowych używany do przechowywania Unicode został zakodowany jako UTF-16LE, typu natywnego znaków w systemach operacyjnych Windows. Wersje znaków typu wide korzystanie z funkcji biblioteki Biblioteka Universal C Runtime (UCRT) **wchar_t** i jego wskaźnika i tablicy typy jako parametrów i zwracanych wartości, jak wersji znaków typu wide natywnego interfejsu API systemu Windows.

**Char16_t** i **char32_t** typy reprezentują odpowiednio 16-bitowe i 32-bitowe znaki dwubajtowe. Unicode zakodowane jako UTF-16, mogą być przechowywane w **char16_t** typu i Unicode zakodowane jako UTF-32 mogą być przechowywane w **char32_t** typu. Parametry te typy i **wchar_t** są wszystkie określone jako *szeroki* ciągów, chociaż termin często dotyczy w szczególności ciągów **wchar_t** typu.

W standardowej bibliotece C++ `basic_string` typu jest przeznaczone dla ciągów zarówno wąskie i dwubajtowe. Użyj `std::string` po znaki są typu **char**, `std::u16string` po znaki są typu **char16_t**, `std::u32string` po znaki są typu **char32_t** , i `std::wstring` po znaki są typu **wchar_t**. Inne typy, które reprezentują tekst, w tym `std::stringstream` i `std::cout` ma specjalizacje wąskie i dwubajtowe ciągów.  
  
