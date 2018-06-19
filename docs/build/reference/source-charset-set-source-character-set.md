---
title: -Źródło-charset (Ustaw zestaw znaków źródła) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- source-charset
- /source-charset
dev_langs:
- C++
helpviewer_keywords:
- /execution-charset compiler option
ms.assetid: d3c5bf7f-526d-4ee4-acc5-c1a02a4fc481
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e4f010eb0f0b83dbc41ebeff624033e59d582535
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379227"
---
# <a name="source-charset-set-source-character-set"></a>/ Source-Charset (Ustaw źródło zestawu znaków)
Pozwala określić źródło zestaw znaków dla pliku wykonywalnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
/source-charset:[IANA_name|.CPID]  
```  
  
## <a name="arguments"></a>Argumenty  
 **IANA_name**  
 Nazwa zestawu znaków zdefiniowany przez organizację IANA.  
  
 **CPID**  
 Identyfikator strony kodu jako liczbę dziesiętną.  
  
## <a name="remarks"></a>Uwagi  
 Można użyć **/Source-Charset** opcję, aby określić zestaw znaków źródła rozszerzone do użycia plików źródłowych zawierają znaki, które nie są reprezentowane w zestawie znaków źródła podstawowych. Zestaw znaków źródła jest kodowanie sposób interpretowania tekst źródłowy programu do reprezentacji wewnętrznej używane jako dane wejściowe fazy wstępnego przetwarzania przed kompilacji. Reprezentacji wewnętrznej jest następnie konwertowana na zestaw znaków wykonania do przechowywania wartości ciągów i znakowe w pliku wykonywalnym. Można użyć albo organizację IANA Nazwa zestawu znaków ISO lub kropkę (.), a następnie identyfikator strony kod dziesiętny 3 do 5 cyfr, aby określić zestaw znaków używany. Zobacz listę obsługiwanych identyfikatorów strony kodu i nazwy zestawu znaków, [kodu strony identyfikatory](http://msdn.microsoft.com/library/windows/desktop/dd317756).  
  
 Domyślnie program Visual Studio wykrywa znacznik kolejności bajtów do ustalenia, czy plik źródłowy jest w zakodowanym formacie Unicode, na przykład UTF-16 lub UTF-8. Jeśli brak znacznika kolejności bajtów zostanie znaleziony, zakłada się plik źródłowy jest zakodowany przy użyciu bieżącej strony kodowej użytkownika, chyba że zostanie określony zbiór znaków nazwy lub kodu strony za pomocą **/Source-Charset** opcji. Program Visual Studio umożliwia zapisanie kodu źródłowego języka C++ za pomocą jednej z kilku kodowanie znaków. Aby uzyskać więcej informacji dotyczących źródła i wykonania zestawów znaków, zobacz [zestawy znaków](../../cpp/character-sets.md) w dokumentacji języka.  
  
 Zestaw znaków źródła, który podasz zamapuj 7-bitowe znaki ASCII punktom kod w zestawie znaków lub mogą wykonać wiele błędów kompilacji. Twoje zestaw znaków źródła musi być również można zmapować do rozszerzonego zestawu można kodować UTF-8 znaków Unicode. Znaki, które nie są można kodować w formacie UTF-8 są reprezentowane przez substitute konkretnej implementacji. Znak zapytania jest używana przez kompilator Microsoft te znaki.  
  
 Jeśli chcesz ustawić zestaw znaków źródła i zestaw znaków wykonania na UTF-8, możesz użyć **/UTF-8** — opcja kompilatora jako skrót. Odpowiada to określenie **/source-charset:utf-8 /execution-charset:utf-8** w wierszu polecenia. Żadnego z tych opcji również umożliwia **Charset** opcji domyślnie.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozwiń węzeł **właściwości konfiguracji**, **C/C++**, **wiersza polecenia** folderu.  
  
3.  W **zaawansowane opcje**, Dodaj **/Source-Charset** opcji, a następnie określ preferowaną metodą kodowania.  
  
4.  Wybierz **OK** Aby zapisać zmiany.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)   
 [/ Execution-Charset (Ustaw wykonywania zestaw znaków)](../../build/reference/execution-charset-set-execution-character-set.md)   
 [/ UTF-8 (Ustaw źródło i plik wykonywalny zestawów znaków UTF-8)](../../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)   
 [/validate-charset (Zweryfikuj zgodność znaków)](../../build/reference/validate-charset-validate-for-compatible-characters.md)