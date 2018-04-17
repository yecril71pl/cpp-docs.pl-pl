---
title: C3850 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: error-reference
f1_keywords:
- C3850
dev_langs:
- C++
helpviewer_keywords:
- C3850
ms.assetid: 028f3a37-f3ad-4ebc-9168-3cdea47524d4
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f5c79f1ab90348ea234e006ae6838d5e80e46c3e
ms.sourcegitcommit: 770f6c4a57200aaa9e8ac6e08a3631a4b4bdca05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="compiler-error-c3850"></a>C3850 błąd kompilatora
"char": universal-character-name Określa nieprawidłowy znak  
  
 Znaki reprezentowany jako uniwersalne nazwy znaków musi reprezentować prawidłowy punktów kodowych Unicode w zakresie 0-10FFFF. Nazwa zawierająca znaki uniwersalne nie może zawierać wartości w zakresie zastępcza Unicode, D800 DFFF lub para zastępcza zakodowany. Kompilator generuje surogatu pary z prawidłowym kodem punktu automatycznie.  
  
 W kodzie skompilowanym c, nazwa zawierająca znaki uniwersalne nie może stanowić znak z zakresu 0000-009F, włącznie z wyjątkiem 0024 ('$'), 0040 ("@") i 0060 ("").  
  
 W kodzie skompilowanym jako C++ nazwa zawierająca znaki uniwersalne może używać dowolnego nieprawidłowy punkt kodu Unicode w ciąg lub literał znakowy. Poza literału nazwa zawierająca znaki uniwersalne nie może stanowić znaku kontrolnego w zakresach 0000 001F lub 007F-009F, włącznie, lub zestaw elementów członkowskich znaku podstawowego źródła.  Aby uzyskać więcej informacji, zobacz [zestawów znaków](../../cpp/character-sets.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3850 i pokazuje, jak rozwiązywanie:  
  
```cpp  
// C3850.cpp  
int main() {  
   int \u0019 = 0;   // C3850, not in allowed range for an identifier  
   const wchar_t * wstr_bad  = L"\UD840DC8A"; // C3850, UCN is surrogate pair  
   const wchar_t * wstr_good = L"\U0002008A"; // Okay, UCN is valid code point  
}  
```