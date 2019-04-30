---
title: Compiler Error C3850
ms.date: 09/05/2018
f1_keywords:
- C3850
helpviewer_keywords:
- C3850
ms.assetid: 028f3a37-f3ad-4ebc-9168-3cdea47524d4
ms.openlocfilehash: 9cd0428726f92c7347b162f74b46035f99cc2d3c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62380958"
---
# <a name="compiler-error-c3850"></a>Compiler Error C3850

> "*char*": universal-character-name Określa nieprawidłowy znak

## <a name="remarks"></a>Uwagi

Reprezentowana jako uniwersalne nazwy znaków musi stanowić prawidłowe punkty kodowe Unicode w zakresie 0-10FFFF znaków. Nazwa znaki uniwersalne nie może zawierać wartości zakresu zastępcze Unicode, D800 DFFF lub para zastępcza zakodowany. Kompilator generuje zastępczy pary z prawidłowym kodem punktu automatycznie.

Kod skompilowany jako C, nazwa znaki uniwersalne nie może stanowić znaku w zakresie 0000-009F włącznie, z wyjątkiem 0024 ('$'), 0040 ("\@") i 0060 ('' ').

W kodzie skompilowany jako języka C++ nazwa znaki uniwersalne może używać dowolnego prawidłowy punkt kodu Unicode w ciągu lub literału znakowego. Poza literału nazwa znaki uniwersalne mogą nie reprezentować znaku kontrolnego w zakresach 0000 001F lub 007F-009F, włącznie, lub ustawić członkiem znaków podstawowgoe źródła.  Aby uzyskać więcej informacji, zobacz [zestawów znaków](../../cpp/character-sets.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C3850 i pokazuje, jak go naprawić:

```cpp
// C3850.cpp
int main() {
   int \u0019 = 0;   // C3850, not in allowed range for an identifier
   const wchar_t * wstr_bad  = L"\UD840DC8A"; // C3850, UCN is surrogate pair
   const wchar_t * wstr_good = L"\U0002008A"; // Okay, UCN is valid code point
}
```