---
title: "-Sprawdź poprawność-charset (weryfikacji zgodne znaków) | Dokumentacja firmy Microsoft"
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
- /validate-charset
- validate-charset
dev_langs: C++
helpviewer_keywords: /validate-charset compiler option
ms.assetid: 50360fd0-4d32-4a4f-95d0-53d38c12ad4c
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7694eb94fe1b50d1892dab399b523a5b0e6deef7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="validate-charset-validate-for-compatible-characters"></a>Charset (weryfikacji zgodne znaków)
Sprawdza, czy tekst źródłowy plik zawiera tylko znaki można przedstawić jako UTF-8.  
  
## <a name="syntax"></a>Składnia  
  
```  
/validate-charset[-]  
```  
  
## <a name="remarks"></a>Uwagi  
 Można użyć **Charset** opcję, aby zweryfikować, że kod źródłowy zawiera tylko znaki, które ma być reprezentowane w znak źródłowy ustawić i zestaw znaków wykonania. Ten test jest włączane automatycznie po określeniu **/Source-Charset**, **/Execution-Charset**, lub **/UTF-8** — opcje kompilatora. Można jawnie wyłączyć ten test, określając **/ validate-charset -** opcji.  
  
 Domyślnie program Visual Studio wykrywa znacznik kolejności bajtów do ustalenia, czy plik źródłowy jest w zakodowanym formacie Unicode, na przykład UTF-16 lub UTF-8. Jeśli brak znacznika kolejności bajtów zostanie znaleziony, zakłada się plik źródłowy jest zakodowany przy użyciu bieżącej strony kodowej użytkownika, chyba że określono stronę kodową przy użyciu **/UTF-8** lub **/Source-Charset** opcji. Program Visual Studio umożliwia zapisanie kodu źródłowego języka C++ za pomocą jednej z kilku kodowanie znaków. Uzyskać informacje o zestawach znaków źródła i wykonania, zobacz [zestawy znaków](../../cpp/character-sets2.md) w dokumentacji języka. Zobacz listę obsługiwanych identyfikatorów strony kodu i nazwy zestawu znaków, [kodu strony identyfikatory](http://msdn.microsoft.com/library/windows/desktop/dd317756).  
  
 Visual Studio będzie korzystać UTF-8 jako kodowania znaków wewnętrzny podczas konwersji między zestaw znaków źródła i zestaw znaków wykonania. Jeśli nie można przedstawić znaku w pliku źródłowym w zestaw znaków wykonania, konwersja UTF-8 zastępuje znak zapytania '?' znaków. **Charset** opcja powoduje, że kompilacji zgłosić ostrzeżenie, jeśli ten problem wystąpi.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozwiń węzeł **właściwości konfiguracji**, **C/C++**, **wiersza polecenia** folderu.  
  
3.  W **zaawansowane opcje**, Dodaj **Charset** opcji, a następnie określ preferowaną metodą kodowania.  
  
4.  Wybierz **OK** Aby zapisać zmiany.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)   
 [/ Execution-Charset (Ustaw wykonywania zestaw znaków)](../../build/reference/execution-charset-set-execution-character-set.md)   
 [/ Source-Charset (Ustaw źródło zestawu znaków)](../../build/reference/source-charset-set-source-character-set.md)   
 [/ UTF-8 (Ustaw źródło i plik wykonywalny zestawów znaków UTF-8)](../../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)