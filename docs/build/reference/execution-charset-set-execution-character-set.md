---
title: — wykonanie-charset (zestaw znaków wykonania zestawu) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- execution-charset
- /execution-charset
dev_langs:
- C++
helpviewer_keywords:
- /execution-charset compiler option
- -execution-charset compiler option
ms.assetid: 0e02f487-2236-45bc-95f3-5760933a8f96
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5bffe1e39aa181a6d53784fbb4501bf8f662b221
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375955"
---
# <a name="execution-charset-set-execution-character-set"></a>/ Execution-Charset (Ustaw wykonywania zestaw znaków)
Umożliwia określenie wykonywania zestaw znaków dla pliku wykonywalnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
/execution-charset:[IANA_name|.CPID]  
```  
  
## <a name="arguments"></a>Argumenty  
 **IANA_name**  
 Nazwa zestawu znaków zdefiniowany przez organizację IANA.  
  
 **CPID**  
 Identyfikator strony kodu.  
  
## <a name="remarks"></a>Uwagi  
 Można użyć **/Execution-Charset** opcję, aby określić zestaw znaków wykonania. Zestaw znaków wykonania jest kodowanie używane do tekstu programu, który jest wprowadzany do fazy kompilacji po wszystkich przetwarzania wstępnego kroki. Zestaw znaków jest używany dla wewnętrznej reprezentacji żadnych ciąg lub znak literałów w kompilowanym kodzie. Ustaw tę opcję, aby określić zestaw znaków wykonania rozszerzonej, aby użyć plików źródłowych zawierają znaki, które nie są można przedstawić w zestaw znaków wykonania podstawowych. Można użyć albo organizację IANA Nazwa zestawu znaków ISO lub kropkę (.), a następnie identyfikator strony kod dziesiętny 3 do 5 cyfr, aby określić zestaw znaków używany. Zobacz listę obsługiwanych identyfikatorów strony kodu i nazwy zestawu znaków, [kodu strony identyfikatory](http://msdn.microsoft.com/library/windows/desktop/dd317756).  
  
 Domyślnie program Visual Studio wykrywa znacznik kolejności bajtów do ustalenia, czy plik źródłowy jest w zakodowanym formacie Unicode, na przykład UTF-16 lub UTF-8. Jeśli zostanie znaleziony Brak znacznika kolejności bajtów, zakłada się plik źródłowy jest zakodowany przy użyciu bieżącej strony kodowej użytkownika, chyba że został określony zbiór znaków nazwy lub kodu strony za pomocą **/Source-Charset** opcji lub **/UTF-8** opcji. Program Visual Studio umożliwia zapisanie kodu źródłowego języka C++ za pomocą jednej z kilku kodowanie znaków. Uzyskać informacje o zestawach znaków źródła i wykonania, zobacz [zestawy znaków](../../cpp/character-sets.md) w dokumentacji języka.  
  
 Jeśli chcesz ustawić zestaw znaków źródła i zestaw znaków wykonania na UTF-8, możesz użyć **/UTF-8** — opcja kompilatora jako skrót. Odpowiada to określenie **/source-charset:utf-8 /execution-charset:utf-8** w wierszu polecenia. Żadnego z tych opcji również umożliwia **Charset** opcji domyślnie.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozwiń węzeł **właściwości konfiguracji**, **C/C++**, **wiersza polecenia** folderu.  
  
3.  W **zaawansowane opcje**, Dodaj **/Execution-Charset** opcji, a następnie określ preferowaną metodą kodowania.  
  
4.  Wybierz **OK** Aby zapisać zmiany.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)   
 [/ Source-Charset (Ustaw źródło zestawu znaków)](../../build/reference/source-charset-set-source-character-set.md)   
 [/ UTF-8 (Ustaw źródło i plik wykonywalny zestawów znaków UTF-8)](../../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)   
 [/validate-charset (Zweryfikuj zgodność znaków)](../../build/reference/validate-charset-validate-for-compatible-characters.md)