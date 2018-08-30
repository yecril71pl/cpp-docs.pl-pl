---
title: -utf-8 (Ustaw źródłowy i wykonywalny zestawów na UTF-8 znaków) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- /utf-8
dev_langs:
- C++
helpviewer_keywords:
- /utf-8 compiler option
ms.assetid: f0e1f3cb-6cae-46eb-9483-04ed13d9b504
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b9002d1989d9f46de29efb7b7c9a940315a99d2b
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43214805"
---
# <a name="utf-8-set-source-and-executable-character-sets-to-utf-8"></a>/ UTF-8 (Ustaw źródłowy i wykonywalny zestaw znaków na UTF-8)
Określa zestaw znaków źródła i zestaw znaków wykonania w formacie UTF-8.  
  
## <a name="syntax"></a>Składnia  
  
```  
/utf-8  
```  
  
## <a name="remarks"></a>Uwagi  
 Możesz użyć **/UTF-8** opcję, aby określić znaków źródła i wykonania ustawia jako zakodowane w formacie UTF-8. Jest równoznaczne z użyciem **/source-charset:utf-8 /execution-charset:utf-8** w wierszu polecenia. Żadnego z tych opcji również włącza **/Validate-Charset** opcja domyślnie. Aby uzyskać listę obsługiwanych identyfikatorami stronę kodu i nazwy zestawu znaków, zobacz [kodu strony identyfikatory](/windows/desktop/Intl/code-page-identifiers).  
  
 Domyślnie program Visual Studio wykrywa znacznika kolejności bajtów, aby określić, czy plik źródłowy jest w formacie zakodowanym Unicode, na przykład, UTF-16 lub UTF-8. Jeśli zostanie znaleziony Brak znacznika kolejności bajtów, zakłada się plik źródłowy jest zakodowane przy użyciu bieżącej stronie kodowej użytkownika, chyba że strona kodowa zostali zdefiniowani za pomocą **/UTF-8** lub **/Source-Charset** opcji. Program Visual Studio umożliwia zapisywanie kodu źródłowego języka C++ za pomocą jednej z kilku kodowania znaków. Aby uzyskać informacji na temat zestawów znaków źródła i wykonania, zobacz [zestawy znaków](../../cpp/character-sets.md) w dokumentacji języka.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozwiń **właściwości konfiguracji**, **C/C++**, **wiersza polecenia** folderu.  
  
3.  W **zaawansowane opcje**, Dodaj **/UTF-8** opcji, a następnie określ preferowany kodowania.  
  
4.  Wybierz **OK** Aby zapisać zmiany.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)   
 [/ Execution-Charset (Ustaw zestaw znaków wykonywania)](../../build/reference/execution-charset-set-execution-character-set.md)   
 [/ Source-Charset (Ustaw źródłowy zestaw znaków)](../../build/reference/source-charset-set-source-character-set.md)   
 [/validate-charset (Zweryfikuj zgodność znaków)](../../build/reference/validate-charset-validate-for-compatible-characters.md)