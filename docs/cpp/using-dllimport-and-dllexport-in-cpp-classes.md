---
title: Korzystanie z dllimport i dllexport w klasach C++
ms.date: 11/04/2016
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
ms.openlocfilehash: 3e8545f058043dfbb8abffc86cf987d0315ba3a7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404679"
---
# <a name="using-dllimport-and-dllexport-in-c-classes"></a>Korzystanie z dllimport i dllexport w klasach C++

## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft

Można zadeklarować klasy C++ za pomocą **dllimport** lub **dllexport** atrybutu. Te formularze znaczą, że cała klasa jest importowana lub eksportowana. Klasy wyeksportowane w ten sposób są nazywane klasy umożliwiające Eksport.

W poniższym przykładzie zdefiniowano klasę można eksportować. Wszystkie jego funkcje składowe i dane statyczne są eksportowane:

```cpp
#define DllExport   __declspec( dllexport )

class DllExport C {
   int i;
   virtual int func( void ) { return 1; }
};
```

Należy pamiętać, że jawne użycie **dllimport** i **dllexport** atrybutów na elementach członkowskich klas eksportowalnych jest zabronione.

##  <a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bdllexportclasses"></a> Klasy dllexport

Kiedy Deklarujesz klasę **dllexport**, wszystkie jej funkcje Członkowskie i Członkowskie dane statyczne są eksportowane. Należy dostarczyć definicje wszystkich takich członków, w tym samym programie. W przeciwnym razie zostanie wygenerowany błąd konsolidatora. Jedynym wyjątkiem od tej reguły mają zastosowanie do czystych funkcji wirtualnych, dla których nie trzeba dostarczyć wyraźnych definicji. Jednakże ponieważ destruktor klasy abstrakcyjnej zawsze jest wywoływany przez destruktor klasy podstawowej, czysto wirtualne destruktory muszą zawsze dostarczać definicję. Należy pamiętać, że te zasady są takie same dla klasy nieeksportowalnej.

W przypadku eksportowania danych typu klasy lub funkcji, które zwracają klasy, pamiętaj wyeksportować klasy.

##  <a name="_pluslang_dllexport_classesdllexportclasses"></a> Klasy dllexport

Kiedy Deklarujesz klasę **dllimport**, wszystkie jej funkcje Członkowskie i Członkowskie dane statyczne są importowane. W odróżnieniu od zachowania **dllimport** i **dllexport** w typach nieklasowych, elementy członkowskie danych statycznych nie można określić definicję w tym samym programie, w którym **dllimport** klasa jest zdefiniowane.

##  <a name="_pluslang_using_dllimport_and_dllexport_in_c2b2binheritanceandexportableclasses"></a> Dziedziczenie i klasy umożliwiające Eksport

Wszystkie klasy podstawowej klasy możliwuje do musi być eksportowalny. W przeciwnym razie kompilator wygeneruje ostrzeżenie. Ponadto wszystkie dostępne elementy członkowskie, które są również klasami musi być eksportowalny. Ta reguła pozwala **dllexport** dziedziczyć od **dllimport** klasy, a **dllimport** dziedziczyć od **dllexport** klasy (ale ten ostatni nie jest zalecane). Zgodnie z zasadą wszystko, co jest dostępne dla klienta biblioteki DLL (według zasady dostępu do C++) powinna być częścią interfejsu, który można. Obejmuje to elementy członkowskie danych prywatnych odwołaniem w funkcjach wbudowanych.

##  <a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bselectivememberimportexport"></a> Selektywny element członkowski importu/eksportu

Ponieważ funkcje składowe i dane statyczne w obrębie klasy niejawnie powiązania zewnętrzne, można zadeklarować je z **dllimport** lub **dllexport** atrybutu, chyba że cała klasa jest eksportowana. Jeśli cała klasa jest importowana lub eksportowana, jawna deklaracja funkcji Członkowskich i dane jako **dllimport** lub **dllexport** jest zabronione. Gdy Deklarujesz element członkowski danych statycznych w ramach definicji klasy jako **dllexport**, definicja musi wystąpić gdzieś w ramach tego samego programu (podobnie jak w przypadku powiązania zewnętrzne nonclass).

Podobnie, można zadeklarować funkcje Członkowskie za pomocą **dllimport** lub **dllexport** atrybutów. W takim przypadku należy podać **dllexport** definicji w obrębie tego samego programu.

Warto zauważyć kilku istotnych kwestiach dotyczących selektywny element członkowski importu i eksportu:

- Selektywny element członkowski importu/eksportu najlepiej nadaje się do dostarczania wersji interfejsu klasy wyeksportowanej, która jest bardziej restrykcyjna; oznacza to jeden dla której można zaprojektować bibliotekę DLL, która udostępnia mniej funkcji publicznych i prywatnych, niż język w przeciwnym razie umożliwia. Jest również przydatny do precyzyjnego dostosowywania interfejsu, który można: gdy wiadomo, że klienta, zgodnie z definicją, nie może uzyskać dostęp do niektórych danych prywatnych, nie trzeba eksportować całej klasy.

- Podczas eksportowania jednej wirtualnej funkcji w klasie, musisz je wszystkie wyeksportować lub przynajmniej dostarczyć wersje, które klient może używać bezpośrednio.

- Jeśli posiadasz klasę, w którym używasz selektywny członkowski import/eksport z funkcjami wirtualnymi, funkcje muszą znajdować się w interfejsu, który można lub zdefiniowanej instrukcji inline (widoczne dla klienta).

- Jeśli zdefiniujesz członka, jak **dllexport** , ale nie umieścisz go w definicji klasy, jest generowany błąd kompilatora. Należy zdefiniować element członkowski w nagłówku klasy.

- Mimo że definicja klasy członków jako **dllimport** lub **dllexport** jest dozwolone, nie może zastąpić interfejsu określonego w definicji klasy.

- Po zdefiniowaniu funkcji członkowskiej w miejscu innym niż ciało definicji klasy, w której została zadeklarowana, generowane jest ostrzeżenie, jeśli funkcja jest zdefiniowana jako **dllexport** lub **dllimport** (jeśli jest to Definicja różni się od określonej w deklaracji klasy).

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[dllexport, dllimport](../cpp/dllexport-dllimport.md)