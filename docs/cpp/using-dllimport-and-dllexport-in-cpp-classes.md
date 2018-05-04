---
title: Korzystanie z dllimport i dllexport w klasach C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- exporting classes [C++]
- declarations [C++], class
- exportable classes [C++]
- classes [C++], declaring
- classes [C++], exportable and inheritance
- inheritance [C++], exportable classes [C++]
- dllimport attribute [C++], classes
- declaring classes [C++]
- dllexport attribute [C++]
- dllexport attribute [C++], classes [C++]
ms.assetid: 8d7d1303-b9e9-47ca-96cc-67bf444a08a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 764ee2026e0ffcd112f202e0d400805c9df55e0b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="using-dllimport-and-dllexport-in-c-classes"></a>Korzystanie z dllimport i dllexport w klasach C++
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 Można zadeklarować klasy C++ z **dllimport** lub `dllexport` atrybutu. Formularze oznacza, że całej klasy jest zaimportować lub wyeksportować. Klasy wyeksportowany w ten sposób są nazywane klasy umożliwiające Eksport.  
  
 W poniższym przykładzie zdefiniowano klasę eksportowalny. Eksportowane są wszystkie jego funkcje Członkowskie i danych statycznych:  
  
```  
#define DllExport   __declspec( dllexport )  
  
class DllExport C {  
   int i;  
   virtual int func( void ) { return 1; }  
};  
```  
  
 Należy zwrócić uwagę że jawne użycie **dllimport** i `dllexport` atrybutów w elementach członkowskich klasy umożliwiające Eksport jest zabronione.  
  
##  <a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bdllexportclasses"></a> dllexport klas  
 Gdy zadeklarować klasy `dllexport`, eksportowane są wszystkie jego funkcje Członkowskie i statyczne elementy członkowskie danych. Należy podać definicje wszystkich tych elementów członkowskich w ten sam program. W przeciwnym razie zostanie wygenerowany błąd konsolidatora. Jedynym wyjątkiem od tej reguły ma zastosowanie do czystych funkcji wirtualnych, dla których nie muszą dostarczać jawne definicje. Jednak ponieważ destruktor dla klasy abstrakcyjnej zawsze jest wywoływana przez destruktor klasy podstawowej, czystej wirtualnej destruktory muszą zawsze podawać definicji. Należy pamiętać, że te reguły są takie same dla klas nonexportable.  
  
 Podczas eksportowania danych typu klasy lub funkcje, które zwracają klasy, należy wyeksportować klasie.  
  
##  <a name="_pluslang_dllexport_classesdllexportclasses"></a> DllImport klasy  
 Gdy zadeklarować klasy **dllimport**, wszystkie jego funkcje Członkowskie i statyczne elementy członkowskie danych są importowane. W przeciwieństwie do zachowania **dllimport** i `dllexport` na typy nonclass statyczne elementy członkowskie danych nie można określić definicję w ten sam program, w którym **dllimport** klasa jest zdefiniowana.  
  
##  <a name="_pluslang_using_dllimport_and_dllexport_in_c2b2binheritanceandexportableclasses"></a> Klasy umożliwiające Eksport i dziedziczenie  
 Wszystkie klasy podstawowe klasy umożliwiające Eksport musi być możliwy do eksportu. W przeciwnym razie generowania ostrzeżeń kompilatora. Ponadto wszystkie dostępne elementy członkowskie, które są również klasy musi być eksportowalny. Ta reguła zezwala `dllexport` klasa dziedziczy po **dllimport** klasy, a **dllimport** klasa dziedziczy po `dllexport` klasy (chociaż to drugie nie jest zalecane). Zgodnie z zasadą dostępnym dla klienta biblioteki DLL (zgodnie z regułami dostępu C++) powinno być częścią można eksportować interfejsu. Obejmuje to dane prywatne elementy członkowskie przywoływany w funkcji śródwierszowych.  
  
##  <a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bselectivememberimportexport"></a> Członek selektywnego Import/Eksport  
 Ponieważ funkcji Członkowskich i danych statycznych w obrębie klasy niejawnie ma połączenie zewnętrzne, mogą zadeklarować je za pomocą **dllimport** lub `dllexport` atrybutu, chyba że całej klasy jest eksportowany. Jeśli całej klasy jest zaimportować lub wyeksportować jawnej deklaracji funkcji Członkowskich i dane jako **dllimport** lub `dllexport` jest zabronione. Jeśli deklaruje element członkowski danych statycznych w definicji klasy jako `dllexport`, definicji musi wystąpić gdzieś w ten sam program (podobnie jak w przypadku nonclass połączenie zewnętrzne).  
  
 Podobnie można zadeklarować elementu członkowskiego ich w funkcji z **dllimport** lub `dllexport` atrybutów. W takim przypadku należy podać `dllexport` definicji w obrębie tego samego programu.  
  
 Warto pamiętać kilka ważne kwestie dotyczące selektywnego — członek, importowanie i eksportowanie:  
  
-   Członek selektywnego importu/eksportu najlepiej nadaje się do dostarczanie wersji interfejsu wyeksportowanej klasy, która jest bardziej restrykcyjne; oznacza to jeden dla którego można zaprojektować bibliotekę DLL, która udostępnia mniej funkcji publiczne i prywatne niż język w przeciwnym razie umożliwia. Jest również przydatne w przypadku dostosowywania interfejsu można eksportować:, gdy wiesz, że klienta, zgodnie z definicją jest w stanie uzyskać dostępu do niektórych danych prywatnych, nie należy wyeksportować całej klasy.  
  
-   Podczas eksportowania jednej funkcji wirtualnych w klasie, możesz wyeksportować wszystkie elementy lub zawiera co najmniej wersji, które klient może używać bezpośrednio.  
  
-   Jeśli masz klasy, w którym za pomocą elementu członkowskiego selektywnego importu/eksportu funkcji wirtualnych funkcji musi być eksportowalny interfejsu lub zdefiniowanymi w tekście (widoczne do klienta).  
  
-   W przypadku definiowania elementu członkowskiego jako `dllexport` , ale nie ma w definicji klasy, zostanie wygenerowany błąd kompilatora. Należy zdefiniować element członkowski w nagłówku klasy.  
  
-   Mimo że definicji elementów członkowskich klasy jako **dllimport** lub `dllexport` jest dozwolone, nie można zastąpić interfejsu określonego w definicji klasy.  
  
-   W miejscu innym niż treści definicji klasy on zadeklarowany w przypadku definiowania funkcji członkowskiej, ostrzeżenie jest generowany, jeśli funkcja jest zdefiniowana jako `dllexport` lub **dllimport** (Jeśli ta definicja różni się od określony w deklaracji klasy).  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [dllexport, dllimport](../cpp/dllexport-dllimport.md)