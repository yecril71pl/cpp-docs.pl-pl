---
title: komentarz (C/C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.comment
- comment_CPP
dev_langs:
- C++
helpviewer_keywords:
- annotations [C++]
- comments [C++], compiled files
- pragmas, comment
- comment pragma
ms.assetid: 20f099ff-6303-49b3-9c03-a94b6aa69b85
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 30683bb76ce674becb81321607bc95fefdb78ac1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="comment-cc"></a>komentarz (C/C++)
Umieszcza rekord komentarz w pliku obiektu lub plik wykonywalny.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
#pragma comment( comment-type [,"commentstring"] )  
```  
  
## <a name="remarks"></a>Uwagi  
 *Typ komentarza* jest jednym z wstępnie zdefiniowane identyfikatory, opisane poniżej, określający typ rekordu komentarza. Opcjonalny `commentstring` jest literałem ciągu zawierający dodatkowe informacje dla niektórych typów komentarza. Ponieważ `commentstring` jest ciągiem literału, jego przestrzega wszystkie reguły dla literałów ciągów względem znaki specjalne, osadzone cudzysłowy (**"**) i łączenia.  
  
 **compiler**  
 Umieszcza nazwę i numer wersji kompilatora w pliku obiektu. Rekord ten komentarz jest ignorowana przez konsolidator. Jeśli podasz `commentstring` parametru dla tego typu rekordu, kompilator generuje ostrzeżenie.  
  
 **exestr**  
 Miejsca `commentstring` w pliku obiektu. W czasie link ten ciąg jest umieszczany w pliku wykonywalnego. Ciąg nie jest ładowany do pamięci podczas ładowania pliku wykonywalnego; jednak można je znaleźć w programie znajduje drukowalnych ciągów w plikach. Jedno użycie dla tego typu rekordu komentarz jest do osadzenia w pliku wykonywalnym numer wersji lub podobne informacje.  
  
 `exestr` jest przestarzałe i zostanie usunięta w przyszłej wersji; konsolidator nie przetwarza rekordów komentarza.  
  
 **lib**  
 Umieszcza rekordu wyszukiwania biblioteki w pliku obiektu. Ten typ komentarza musi towarzyszyć `commentstring` parametr zawierający nazwę (i prawdopodobnie ścieżki) biblioteki, która ma konsolidatora do wyszukiwania. Biblioteka wyszukiwania domyślne rekordy w pliku obiektu; następuje nazwa biblioteki konsolidator wyszukiwania dla tej biblioteki, tak jakby było nazwane go w wierszu polecenia pod warunkiem, że biblioteka nie zostanie określony z [/nodefaultlib](../build/reference/nodefaultlib-ignore-libraries.md). Wiele rekordów wyszukiwania biblioteki można umieścić w tym samym pliku źródłowego; Każdy rekord występuje w pliku obiektu w tej samej kolejności napotkano w pliku źródłowym.  
  
 Jeśli kolejność domyślnej biblioteki i Biblioteka dodano odgrywa ważną rolę, kompilowania przy użyciu [/Zl](../build/reference/zl-omit-default-library-name.md) przełącznika uniemożliwi umieszczany w module obiektu domyślną nazwę biblioteki. Drugi pragma komentarz można następnie używany do Wstaw nazwę domyślnej biblioteki po dodanych biblioteki. Bibliotek na liście z tych pragm pojawi się w module obiektu w tej samej kolejności, które zostały znalezione w kodzie źródłowym.  
  
 **linker**  
 Miejsca [— opcja konsolidatora](../build/reference/linker-options.md) w pliku obiektu. Typ komentarza umożliwia określanie opcji konsolidatora zamiast przekazanie jej do wiersza polecenia lub określając go w środowisku programistycznym. Na przykład można określić / include — opcja, wymuszenie włączenia symbolu:  
  
```  
#pragma comment(linker, "/include:__mySymbol")  
```  
  
 Tylko następujące (*typ komentarza*) mają być przekazane do identyfikatora konsolidatora dostępnych opcji konsolidatora:  
  
-   [/DEFAULTLIB](../build/reference/defaultlib-specify-default-library.md)  
  
-   [/EXPORT](../build/reference/export-exports-a-function.md)  
  
-   [/INCLUDE](../build/reference/include-force-symbol-references.md)  
  
-   [/ MANIFESTDEPENDENCY](../build/reference/manifestdependency-specify-manifest-dependencies.md)  
  
-   [/MERGE](../build/reference/merge-combine-sections.md)  
  
-   [/ SECTION](../build/reference/section-specify-section-attributes.md)  
  
 **Użytkownika**  
 Umieszcza ogólne komentarze w pliku obiektu. `commentstring` Parametr zawiera tekst komentarza. Rekord ten komentarz jest ignorowana przez konsolidator.  
  
 Następujące pragma powoduje, że konsolidator, aby wyszukać EMAPI. Biblioteki LIB podczas konsolidacji. Konsolidator przeszukuje najpierw w bieżącym katalogu roboczym, a następnie w ścieżce określonej w zmiennej środowiskowej LIB.  
  
```  
#pragma comment( lib, "emapi" )  
```  
  
 Następujące pragma powoduje, że kompilator umieszcza nazwę i numer wersji kompilatora w pliku obiektu:  
  
```  
#pragma comment( compiler )  
```  
  
> [!NOTE]
>  Dla komentarzy które trwają `commentstring` parametru, można użyć makra w dowolnym miejscu, w której można zastosować literału ciągu, pod warunkiem, że makro rozwijany do literału ciągu. Można także połączyć dowolną kombinację literały i makra, które Rozwiń, aby literałów ciągów. Na przykład następująca instrukcja jest dopuszczalne:  
  
```  
#pragma comment( user, "Compiled on " __DATE__ " at " __TIME__ )   
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)