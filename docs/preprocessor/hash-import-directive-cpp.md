---
title: "#Importuj — dyrektywa (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: '#import'
dev_langs: C++
helpviewer_keywords:
- .tlh files
- '#import directive'
- import directive (#import)
- tlh files
- tlbid switch
- preprocessor, directives
- COM, type library header file
ms.assetid: 787d1112-e543-40d7-ab15-a63d43f4030a
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3d104f25dfc45a0d2b24650289b6ce49f8468c39
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="import-directive-c"></a>#import — dyrektywa (C++)
**Określonego języka C++**  
  
 Używane w celu uwzględnienia informacji z biblioteki typów. Zawartość biblioteki typów jest konwertowany na klasach C++, przede wszystkim opisujące interfejsy modelu COM.  
  
## <a name="syntax"></a>Składnia  
  
```  
#import "filename" [attributes]  
#import <filename> [attributes]  
```  
  
#### <a name="parameters"></a>Parametry  
 *Nazwa pliku*  
 Określa bibliotekę typów, aby zaimportować. `filename`może to być jedna z następujących czynności:  
  
-   Nazwa pliku, który zawiera bibliotekę typów, takich jak plik .olb, .tlb lub dll. Słowo kluczowe **plik:**, mogą występować przed nazw plików.  
  
-   Progid kontrolki w bibliotece typów. Słowo kluczowe **progid:**, mogą występować przed każdym progid. Na przykład:  
  
    ```  
    #import "progid:my.prog.id.1.5"  
    ```  
  
     Aby uzyskać więcej informacji na temat ProgID, zobacz [określenie Identyfikatora lokalizacji i numer wersji](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber).  
  
     Należy pamiętać, że podczas kompilowania przy użyciu kompilatora krzyżowego na 64-bitowym systemie operacyjnym, kompilator będzie mogła odczytywać tylko gałęzi rejestru w 32-bitowych. Można użyć natywny kompilator 64-bitowy kompilacji i rejestrowanie biblioteki typów 64-bitowych.  
  
-   Identyfikator biblioteki biblioteki typów. Słowo kluczowe **identyfikator biblioteki:**, może występować przed każdym identyfikator biblioteki. Na przykład:  
  
    ```  
    #import "libid:12341234-1234-1234-1234-123412341234" version("4.0") lcid("9")  
    ```  
  
     Jeśli nie określisz wersji lub identyfikator lcid, [reguły](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber) stosowane do **progid:** również są stosowane do **identyfikatora libid:**.  
  
-   Plik wykonywalny (.exe).  
  
-   Plik biblioteki (.dll) zawierający typ zasobu biblioteki (na przykład ocx).  
  
-   Złożone dokument zawierający biblioteki typów.  
  
-   Inny format pliku, który zostały zrozumiane przez **LoadTypeLib** interfejsu API.  
  
 `attributes`  
 Co najmniej jeden [atrybuty #import](#_predir_the_23import_directive_import_attributes). Oddzielne atrybuty spacjami lub przecinkami. Na przykład:  
  
```  
#import "..\drawctl\drawctl.tlb" no_namespace, raw_interfaces_only  
```  
  
 —lub—  
  
```  
#import "..\drawctl\drawctl.tlb" no_namespace raw_interfaces_only  
```  
  
## <a name="remarks"></a>Uwagi  
  
##  <a name="_predir_the_23import_directive_searchorderforfilename"></a>Kolejność wyszukiwania dla nazwy pliku  
 *Nazwa pliku* opcjonalnie jest poprzedzony specyfikacji katalogu. Nazwa pliku nazwę istniejącego pliku. Różnica między dwie formy składni jest kolejność wyszukiwania preprocesora typu plików bibliotek, gdy nie w pełni określono ścieżkę.  
  
|Składnia formularza|Akcja|  
|-----------------|------------|  
|Formularz cudzysłowie|Powoduje, że preprocesora do wyszukiwania plików bibliotek typu najpierw w katalogu pliku, który zawiera `#import` instrukcji, a następnie w katalogach niezależnie od plików, które zawierają (`#include`) tego pliku. Preprocesora wyszukuje wzdłuż ścieżki pokazano poniżej.|  
|Formularz nawiasu ostrego|Powoduje, że preprocesora do wyszukiwania plików bibliotek typu wzdłuż następujące ścieżki:<br /><br /> 1.  **Ścieżki** listy ścieżek zmiennej środowiskowej<br />2.  **LIB** listy ścieżek zmiennej środowiskowej<br />3.  Ścieżka określona przez /I (dodatkowe katalogi dołączenia) — opcja kompilatora, ale kompilator szuka biblioteki typów, której odwoływało się z inną biblioteką typów z [no_registry](../preprocessor/no-registry.md) atrybutu.|  
  
##  <a name="_predir_the_23import_directive_specifyingthelocalizationidandversionnumber"></a>Określenie Identyfikatora lokalizacji i numer wersji  
 Po określeniu identyfikatora progid, można również określić lokalizacja identyfikator i numer wersji programu. Na przykład:  
  
```  
#import "progid:my.prog.id" lcid("0") version("4.0)  
```  
  
 Jeśli nie określisz identyfikator lokalizacji, identyfikatora progid jest wybierany zgodnie z następującymi zasadami:  
  
-   Jeśli istnieje tylko jeden identyfikator lokalizacji, co jest używany.  
  
-   Jeśli istnieje więcej niż jeden identyfikator lokalizacji, pierwsza z nich z numerem wersji 0, 9 lub 409 jest używany.  
  
-   Jeśli istnieje więcej niż jeden identyfikator lokalizacji, żaden z nich nie jest równa 0, 9 lub 409 ostatnią jest używany.  
  
-   Jeśli nie określisz numeru wersji, jest używana najnowsza wersja.  
  
##  <a name="_predir_the_23import_directive_header_files_created_by_import"></a>Utworzone przez Import pliki nagłówka  
 `#import`tworzy dwa pliki nagłówkowe, które rekonstrukcji zawartości biblioteki typu kodu źródłowego języka C++. Plik nagłówka podstawowy jest podobny do wytworzonego przez kompilator Microsoft interfejsu Definition Language (MIDL), ale dodatkowy kod wygenerowany przez kompilator i danych. [Pliku nagłówka głównej](#_predir_the_primary_type_library_header_file) ma taką samą nazwę podstawową jak biblioteki typów plus. Tlh — rozszerzenie. Plik nagłówka dodatkowej ma taką samą nazwę podstawową jak biblioteki typów z. Rozszerzenie TLI. Zawiera implementacji dla funkcji Członkowskich generowane przez kompilator i jest dołączany (`#include`) w pliku nagłówka podstawowego.  
  
 W przypadku importowania dispinterface właściwości, która korzysta z parametrami byref #import nie będą generowane __declspec ([właściwości](../cpp/property-cpp.md)) instrukcji dla funkcji.  
  
 Oba pliki nagłówka są umieszczane w katalogu danych wyjściowych określonego przez opcję /Fo (nazwa pliku obiektu). Są następnie odczytu i kompilowany przez kompilator tak, jakby plik nagłówka podstawowy został o nazwie `#include` dyrektywy.  
  
 Dołączono następujące optymalizacje kompilatora `#import` dyrektywy:  
  
-   Plik nagłówka, podczas tworzenia, znajduje się tą samą sygnaturą czasową jako biblioteki typów.  
  
-   Gdy `#import` jest przetwarzane, kompilator najpierw sprawdza nagłówka istnieje i czy jest aktualny. Jeśli tak, następnie go nie musi zostać utworzony ponownie.  
  
 `#import` Dyrektywy również uczestniczy w minimalna ponowna kompilacja i można umieścić w pliku prekompilowanego nagłówka. Zobacz [tworzenie prekompilowanych plików nagłówka](../build/reference/creating-precompiled-header-files.md) Aby uzyskać więcej informacji.  
  
###  <a name="_predir_the_primary_type_library_header_file"></a>Plik nagłówka biblioteki typu podstawowego  
 Plik nagłówka biblioteki typu podstawowego składa się z siedmiu sekcji:  
  
-   Standardowy nagłówek: składa się z komentarzami, `#include` instrukcji dla COMDEF. H (który definiuje niektóre standardowe makra używane w nagłówku) oraz inne informacje różne ustawienia.  
  
-   Przekazuj odniesienia i definicje typów: składa się z deklaracje struktur, takich jak `struct IMyInterface` i definicje typów.  
  
-   Deklaracje wskaźników inteligentne: klasy szablonu `_com_ptr_t` jest implementacją inteligentnych wskaźnika, który hermetyzuje wskaźniki interfejsu i eliminuje konieczność kontaktowania się `AddRef`, **wersji**, `QueryInterface` funkcji. Ponadto ukrywa `CoCreateInstance` wywołań podczas tworzenia nowego obiektu COM. Ta sekcja używa instrukcji makro **_COM_SMARTPTR_TYPEDEF** ustanowienie definicje typów interfejsów modelu COM jako szablon specjalizacjach [_com_ptr_t —](../cpp/com-ptr-t-class.md) klasy szablonu. Na przykład dla interfejsu **IMyInterface**,. Tlh — plik będzie zawierać:  
  
    ```  
    _COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));  
    ```  
  
     które kompilator będzie Rozwiń do:  
  
    ```  
    typedef _com_ptr_t<_com_IIID<IMyInterface, __uuidof(IMyInterface)> > IMyInterfacePtr;  
    ```  
  
     Typ `IMyInterfacePtr` mogą być następnie używane zamiast wskaźnik interfejsu pierwotnego `IMyInterface*`. W rezultacie nie istnieje potrzeba do wywołania poszczególnych **IUnknown** funkcje Członkowskie  
  
-   Deklaracje TypeInfo: zawiera głównie definicje klas i inne elementy udostępnianie typeinfo poszczególnych elementów zwróconych przez **ITypeLib:GetTypeInfo**. W tej sekcji, każdy element typeinfo z biblioteki typów jest uwzględniana w nagłówka w postaci zależny od `TYPEKIND` informacji.  
  
-   Opcjonalne określanie identyfikatora GUID w starym stylu: zawiera inicjowanie stałe nazwane identyfikatora GUID. Są to nazwy w postaci **CLSID_CoClass** i **IID_Interface**, podobnie jak wygenerowanymi przez kompilator MIDL.  
  
-   `#include`Instrukcja dla nagłówka typu dodatkowej biblioteki.  
  
-   Standardowa stopka: obecnie `#pragma pack(pop)`.  
  
 Wszystkie sekcje, z wyjątkiem nagłówek standardowa stopka standardowej sekcji i są ujęte w przestrzeni nazw z jego nazwa określona przez **biblioteki** instrukcji w oryginalnym pliku IDL. Jawna kwalifikacja z nazwą przestrzeni nazw lub przy tym następującą instrukcję, można użyć nazwy z nagłówka biblioteki typów:  
  
```  
using namespace MyLib;  
```  
  
 natychmiast po `#import` instrukcji w kodzie źródłowym.  
  
 Przestrzeń nazw, można pominąć przy użyciu [no_namespace —](#_predir_no_namespace) atrybutu `#import` dyrektywy. Jednak pomijanie przestrzeni nazw może prowadzić do konfliktów nazw. Przestrzeń nazw również można zmienić nazwy przez [rename_namespace —](#_predir_rename_namespace) atrybutu.  
  
 Kompilator zapewnia pełną ścieżkę do dowolnego typu zależności biblioteki wymagane przez bibliotekę typów, które są obecnie przetwarzane. Ścieżka są zapisywane, w formie komentarzy w nagłówku biblioteki typów (. Tlh —) czy kompilator generuje dla każdego przetwarzane biblioteki typów.  
  
 Jeśli biblioteki typów zawiera odwołania do typów zdefiniowanych w innych bibliotek typów, a następnie. Tlh — plik będzie zawierać komentarzy następującego sortowania:  
  
```  
//  
// Cross-referenced type libraries:  
//  
//  #import "c:\path\typelib0.tlb"  
//  
```  
  
 Nazwa pliku w `#import` komentarz jest pełna ścieżka Biblioteka typów odsyłaczy przechowywanej w rejestrze. Jeśli wystąpią błędy, które są z powodu braku definicji typu, sprawdź komentarze na nagłówek. Tlh — aby zobaczyć, które biblioteki typów zależnych, należy najpierw zaimportować. Błędy składniowe (na przykład C2143, C2146, C2321), są prawdopodobnie błędy C2501 (Brak specyfikatory decl), lub C2433 ("inline" nie jest dozwolone w deklaracji danych) podczas kompilowania. Plik TLI.  
  
 Należy określić, który zależności komentarze nie są w innym przypadku przewidziane przez system nagłówków, a następnie podaj `#import` dyrektywy w pewnym momencie przed `#import` dyrektywy biblioteki typów zależnych naprawić błędy.  
  
 Aby uzyskać więcej informacji, zobacz artykuł bazy wiedzy Knowledge Base "#import otoki metody może spowodować naruszenie zasad dostępu" (Q242527) lub "błędy kompilatora, korzystając z #import XML" (Q269194). Artykuły bazy wiedzy można znaleźć na nośniku w bibliotece MSDN lub na [Microsoft Support](https://support.microsoft.com/).  
  
##  <a name="_predir_the_23import_directive_import_attributes"></a>atrybuty #import  
 `#import`Opcjonalnie można dodać jeden lub więcej atrybutów. Te atrybuty Poinformuj kompilator, aby zmodyfikować zawartość z nagłówków biblioteki typów. Ukośnik odwrotny (**\\**) symbol można uwzględnić dodatkowe wiersze w jednej `#import` instrukcji. Na przykład:  
  
```  
#import "test.lib" no_namespace \  
   rename("OldName", "NewName")  
```  
  
 Aby uzyskać więcej informacji, zobacz [atrybuty #import](../preprocessor/hash-import-attributes-cpp.md).  
  
 **KOŃCOWY określonego języka C++**  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md)   
 [Obsługa kompilatora COM](../cpp/compiler-com-support.md)
