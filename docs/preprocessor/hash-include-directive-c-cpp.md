---
title: '#include — dyrektywa (C/C++) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '#include'
dev_langs:
- C++
helpviewer_keywords:
- preprocessor, directives
- '#include directive'
- include directive (#include)
ms.assetid: 17067dc0-8db1-4f2d-b43e-ec12ecf83238
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 64cd6098f7a539fd883a9c8e0e0c116590a2f38f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33843551"
---
# <a name="include-directive-cc"></a>#include — dyrektywa (C/C++)
Określa, że na traktowanie zawartość określonego pliku, tak jakby pojawią się one w programie źródłowym w momencie, w którym pojawi się dyrektywy preprocesora.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      #include  "path-spec"  
#include  <path-spec>  
```  
  
## <a name="remarks"></a>Uwagi  
 Można zorganizować definicje stała i makra do plików dołączanych, a następnie użyć `#include` dyrektywy, aby dodać je do dowolnego pliku źródłowego. Obejmują pliki są także przydatne w przypadku włączania deklaracje zmiennych zewnętrznych i złożone typy danych. Typy mogą być zdefiniowane i o nazwie tylko raz w pliku dołączenia utworzone w tym celu.  
  
 `path-spec` Jest nazwą pliku, który opcjonalnie może być poprzedzony specyfikacji katalogu. Nazwa pliku nazwę istniejącego pliku. Składnia `path-spec` zależy od systemu operacyjnego, na którym program ma być kompilowana.  
  
 Aby uzyskać informacje o sposobie odwołuje się do zestawów w aplikacji C++, która ma być kompilowana przy użyciu [/CLR](../build/reference/clr-common-language-runtime-compilation.md), zobacz [#using](../preprocessor/hash-using-directive-cpp.md).  
  
 Oba formularze składni spowodować tej dyrektywy, które mają zostać zastąpione przez całą zawartość pliku dołączanego określony. Różnica między dwoma formularzami jest kolejność wyszukiwania preprocesora dla pliki nagłówkowe, gdy nie w pełni określono ścieżkę. W poniższej tabeli przedstawiono różnicę między dwoma formularzami składni.  
  
|Składnia formularza|Akcja|  
|-----------------|------------|  
|Formularz cudzysłowie|Preprocesora wyszukiwania plików dołączanych w następującej kolejności:<br /><br /> 1) w tym samym katalogu co plik, który zawiera `#include` instrukcji.<br /><br /> 2) w katalogach aktualnie otwartą obejmują pliki w odwrotnej kolejności, w jakiej były otwierane. Wyszukiwanie rozpoczyna się w katalogu nadrzędnego plik dołączany i kontynuuje w górę za pośrednictwem katalogi ponadnadrzędny wszelkie pliki dołączane.<br /><br /> 3) na ścieżce określonej przez każdego /I — opcja kompilatora.<br /><br /> 4)<br /><br /> Wzdłuż ścieżki, które są określone przez zmienną środowiskową INCLUDE.|  
|Formularz nawiasu ostrego|Preprocesora wyszukiwania plików dołączanych w następującej kolejności:<br /><br /> 1) na ścieżce określonej przez każdego /I — opcja kompilatora.<br /><br /> 2) podczas kompilowania występuje w wierszu polecenia wzdłuż ścieżki, które są określone przez zmienną środowiskową INCLUDE.|  
  
 Zatrzymuje preprocesora, wyszukiwanie jak znajdzie pliku o podanej nazwie. Jeśli ujmij określenia ścieżki pełne, jednoznaczne dla dołączanego pliku w podwójnym cudzysłowie (""), preprocesora wyszukuje tej specyfikacji ścieżki i ignoruje standardowe katalogi.  
  
 Jeśli nazwa pliku, który został ujęty w podwójny cudzysłów specyfikacji ścieżki niekompletne, pierwszego preprocesora wyszukuje katalog pliku "elementu nadrzędnego". Nadrzędnego pliku to plik, który zawiera `#include` dyrektywy. Na przykład, jeśli zawiera plik o nazwie `file2` w pliku o nazwie `file1`, `file1` jest pliku nadrzędnym.  
  
 Dołącz pliki mogą być "nested"; oznacza to `#include` dyrektywa może występować w pliku o nazwie przez inną `#include` dyrektywy. Na przykład `file2` mogą obejmować `file3`. W takim przypadku `file1` nadal będzie nadrzędny `file2`, ale byłoby "ponadnadrzędny" z `file3`.  
  
 Gdy obejmują pliki są zagnieżdżone i podczas kompilowania kodu w wierszu polecenia, wyszukiwanie w katalogu rozpoczyna się od katalogi pliku nadrzędnego i następnie obejmującego katalogi plików nadrzędny. Oznacza to, że wyszukiwanie rozpoczyna się względem katalogu, który zawiera źródła, które jest obecnie przetwarzane. Jeśli plik nie zostanie znaleziony, wyszukiwanie przenosi do katalogów, które są określone przez /I — opcja kompilatora. Na koniec katalogi, które są określone przez zmienną środowiskową INCLUDE są przeszukiwane.  
  
 Środowiska programowania zmiennej środowiskowej INCLUDE jest ignorowana. Informacje dotyczące sposobu konfigurowania katalogi, które są wyszukiwane pliki nagłówkowe — dotyczy to również lib — zmienna środowiskowa — zobacz [strona właściwości katalogów VC ++](../ide/vcpp-directories-property-page.md).  
  
 Ten przykład przedstawia dołączania plików przy użyciu nawiasy:  
  
```  
#include <stdio.h>  
```  
  
 W tym przykładzie dodaje zawartość pliku o nazwie stdio —. H, aby program źródłowy. Nawiasu ostrego spowodować preprocesora do wyszukiwania katalogi, które są określone przez zmienną środowiskową INCLUDE dla stdio —. H, po przeszukuje katalogi, które są określone przez /I — opcja kompilatora.  
  
 W kolejnym przykładzie pokazano dołączania plików za pomocą formularza ujętego w cudzysłów:  
  
```  
#include "defs.h"  
```  
  
 W tym przykładzie dodaje zawartość pliku, określonej przez DEFS. H, aby program źródłowy. Cudzysłów oznacza, że preprocesora przeszukuje najpierw katalog, który zawiera plik źródłowy nadrzędnej.  
  
 Zagnieżdżanie plików dołączanych, można nadal maksymalnie 10 poziomów. Gdy zagnieżdżony `#include` jest przetwarzane, preprocesora w dalszym ciągu wstawić otaczającego pliku dołączanego do oryginalnego pliku źródłowego.  
  
 **Microsoft Specific**  
  
 Aby zlokalizować pliki źródłowe includable, preprocesora najpierw przeszukuje katalogi, które są określone przez /I — opcja kompilatora. Jeśli opcja nie istnieje lub nie powiedzie się, preprocesora użycie zmiennej środowiskowej INCLUDE można znaleźć żadnych plików dołączanych w nawiasy. Dołącz środowiska zmienną i /I — opcja kompilatora może zawierać wiele ścieżek rozdzielonych średnikami (;). Jeśli więcej niż jeden katalog jest wyświetlany jako część opcji /I lub w zmiennej środowiskowej INCLUDE, preprocesora przeszukuje je w kolejności ich występowania.  
  
 Na przykład, polecenie  
  
```  
CL /ID:\MSVC\INCLUDE MYPROG.C  
```  
  
 powoduje, że preprocesora wyszukać w katalogu D:\MSVC\INCLUDE\ plików dołączanych, takich jak stdio —. H. Polecenia  
  
```  
SET INCLUDE=D:\MSVC\INCLUDE  
CL MYPROG.C  
```  
  
 mają ten sam efekt. Jeśli oba zestawy wyszukiwanie nie powiedzie się, zostanie wygenerowany błąd krytyczny kompilatora.  
  
 Jeśli nazwa pliku jest całkowicie określone dla dołączanego pliku, który ma ścieżkę zawierającą dwukropkiem (na przykład F:\MSVC\SPECIAL\INCL\TEST. H) wynika preprocesora, ścieżki.  
  
 Dla plików dołączanych, które są określone jako `#include` "`path-spec`", wyszukiwanie w katalogu rozpoczyna się od katalogu pliku nadrzędnego i następnie obejmującego katalogi plików nadrzędny. Oznacza to, że wyszukiwanie rozpoczyna się względem katalogu, który zawiera plik źródłowy, który zawiera `#include` dyrektywy przetwarzany. Jeśli plik nadrzędny nie istnieje i nie znaleziono pliku, wyszukiwanie jest kontynuowane tak, jakby nazwa pliku są ujęte w nawiasy.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md)