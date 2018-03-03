---
title: "-utf-8 (Ustaw źródło i plik wykonywalny znak zestawów do UTF-8) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /utf-8
dev_langs:
- C++
helpviewer_keywords:
- /utf-8 compiler option
ms.assetid: f0e1f3cb-6cae-46eb-9483-04ed13d9b504
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 592cba779113a6658b40d0dc3f855f53fa3d170c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="utf-8-set-source-and-executable-character-sets-to-utf-8"></a>/ UTF-8 (Ustaw źródło i plik wykonywalny zestawów znaków UTF-8)
Określa zestaw znaków źródła i zestaw znaków wykonania jako UTF-8.  
  
## <a name="syntax"></a>Składnia  
  
```  
/utf-8  
```  
  
## <a name="remarks"></a>Uwagi  
 Można użyć **/UTF-8** opcję, aby określić znak źródłowym i wykonywania ustawia jako zakodowany przy użyciu UTF-8. Odpowiada to określenie **/source-charset:utf-8 /execution-charset:utf-8** w wierszu polecenia. Żadnego z tych opcji również umożliwia **Charset** opcji domyślnie. Zobacz listę obsługiwanych identyfikatorów strony kodu i nazwy zestawu znaków, [kodu strony identyfikatory](http://msdn.microsoft.com/library/windows/desktop/dd317756).  
  
 Domyślnie program Visual Studio wykrywa znacznik kolejności bajtów do ustalenia, czy plik źródłowy jest w zakodowanym formacie Unicode, na przykład UTF-16 lub UTF-8. Jeśli brak znacznika kolejności bajtów zostanie znaleziony, zakłada się plik źródłowy jest zakodowany przy użyciu bieżącej strony kodowej użytkownika, chyba że określono stronę kodową przy użyciu **/UTF-8** lub **/Source-Charset** opcji. Program Visual Studio umożliwia zapisanie kodu źródłowego języka C++ za pomocą jednej z kilku kodowanie znaków. Uzyskać informacje o zestawach znaków źródła i wykonania, zobacz [zestawy znaków](../../cpp/character-sets2.md) w dokumentacji języka.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozwiń węzeł **właściwości konfiguracji**, **C/C++**, **wiersza polecenia** folderu.  
  
3.  W **zaawansowane opcje**, Dodaj **/UTF-8** opcji, a następnie określ preferowaną metodą kodowania.  
  
4.  Wybierz **OK** Aby zapisać zmiany.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)   
 [/ Execution-Charset (Ustaw wykonywania zestaw znaków)](../../build/reference/execution-charset-set-execution-character-set.md)   
 [/ Source-Charset (Ustaw źródło zestawu znaków)](../../build/reference/source-charset-set-source-character-set.md)   
 [/validate-charset (Zweryfikuj zgodność znaków)](../../build/reference/validate-charset-validate-for-compatible-characters.md)