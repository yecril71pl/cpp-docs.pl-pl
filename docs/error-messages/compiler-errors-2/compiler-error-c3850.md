---
title: Błąd kompilatora C3850
ms.date: 09/05/2018
f1_keywords:
- C3850
helpviewer_keywords:
- C3850
ms.assetid: 028f3a37-f3ad-4ebc-9168-3cdea47524d4
ms.openlocfilehash: 5de7994e8bf46105e94271ab29bf9e27f1da3e76
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165568"
---
# <a name="compiler-error-c3850"></a>Błąd kompilatora C3850

> "*char*": nazwa typu uniwersalnego określa nieprawidłowy znak

## <a name="remarks"></a>Uwagi

Znaki reprezentowane jako uniwersalne nazwy znaków muszą reprezentować prawidłowe punkty kodu Unicode w zakresie 0 – 10FFFF. Nazwa znaku uniwersalnego nie może zawierać wartości w zakresie surogatu Unicode, D800-DFFF ani zakodowanej pary zastępczej. Kompilator generuje parę surogatów z prawidłowego punktu kodu.

W kodzie skompilowanym jako C, uniwersalna nazwa znaku nie może reprezentować znaku w zakresie 0000-009F, włącznie, z wyjątkami 0024 ("$"), 0040 ("\@") i 0060 ("" ").

W kodzie skompilowanym C++jako, uniwersalna nazwa znaku może używać dowolnego prawidłowego punktu kodu Unicode w ciągu lub w literale znakowym. Poza literałem, uniwersalna nazwa znaku nie może reprezentować znaku kontrolnego w zakresach 0000-001F lub 007F-009F, zarówno włącznie, jak i elementów członkowskich podstawowego zestawu znaków źródłowych.  Aby uzyskać więcej informacji, zobacz [zestawy znaków](../../cpp/character-sets.md).

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
