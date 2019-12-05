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
ms.openlocfilehash: b42ba7c1a88a4de28eb3385bbf6cad068abf1944
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857232"
---
# <a name="using-dllimport-and-dllexport-in-c-classes"></a>Korzystanie z dllimport i dllexport w klasach C++

**Microsoft Specific**

Można zadeklarować C++ klasy z atrybutem **dllimport** lub **dllexport** . Te formularze znaczą, że cała klasa jest zaimportowana lub wyeksportowana. Klasy wyeksportowane w ten sposób są nazywane klasami, które można eksportować.

W poniższym przykładzie zdefiniowano klasę, którą można eksportować. Wszystkie jego funkcje składowe i dane statyczne są eksportowane:

```cpp
#define DllExport   __declspec( dllexport )

class DllExport C {
   int i;
   virtual int func( void ) { return 1; }
};
```

Należy zauważyć, że jawne użycie atrybutów **dllimport** i **dllexport** na elementach członkowskich klasy możliwej do eksportu jest zabronione.

##  <a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bdllexportclasses"></a>Klasy dllexport

Kiedy deklarujesz klasę **dllexport**, wszystkie jej funkcje członkowskie i statyczne składowe danych są eksportowane. Należy dostarczyć definicje wszystkich takich członków w tym samym programie. W przeciwnym wypadku zostanie wygenerowany błąd konsolidatora. Jeden wyjątek od tej reguły odnosi się do czystych funkcji wirtualnych, dla których nie trzeba dostarczyć wyraźnych definicji. Jednak, ponieważ destruktor klasy abstrakcyjnej zawsze jest wywoływany przez destruktor klasy podstawowej, czysto wirtualne destruktory muszą zawsze dostarczać definicję. Należy zauważyć, że te zasady są takie same dla klasy nieeksportowalnej.

Podczas eksportowania danych typu klasy lub funkcji, które zwracają klasy, należy wyeksportować klasy.

##  <a name="_pluslang_dllexport_classesdllexportclasses"></a>Klasy dllimport

Podczas deklarowania klasy **dllimport**, wszystkie jej funkcje członkowskie i statyczne składowe danych są importowane. W przeciwieństwie do zachowania elementu **dllimport** i **dllexport** w typach nieklasowych, statyczne składowe danych nie mogą określać definicji w tym samym programie, w którym zdefiniowano klasę **dllimport** .

##  <a name="_pluslang_using_dllimport_and_dllexport_in_c2b2binheritanceandexportableclasses"></a>Dziedziczenie i możliwe do eksportowania klasy

Wszystkie klasy podstawowej klasy możliwuje do eksportowania muszą być możliwe do eksportowania. Jeśli nie, kompilator wygeneruje ostrzeżenie. Ponadto wszystkie dostępne elementy członkowskie, które są również klasami muszą być możliwe do eksportowania. Ta reguła zezwala klasie **dllexport** na dziedziczenie z klasy **dllimport** i klasy **dllimport** do dziedziczenia z klasy **dllexport** (mimo że nie jest to zalecane). Co do zasady, wszystko, co jest dostępne dla klienta biblioteki DLL (według zasady dostępu do C++) powinno być częścią interfejsu, który można eksportować. Obejmuje to elementy członkowskie danych prywatnych z odwołaniem w funkcjach wbudowanych.

##  <a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bselectivememberimportexport"></a>Selektywny element członkowski importu/eksportu

Ponieważ funkcje składowe i dane statyczne w klasie niejawnie mają powiązania zewnętrzne, można je zadeklarować przy użyciu atrybutu **dllimport** lub **dllexport** , chyba że cała klasa zostanie wyeksportowana. W przypadku zaimportowania lub wyeksportowania całej klasy, jawna deklaracja funkcji składowych i danych jako **dllimport** lub **dllexport** jest zabroniona. Jeśli zadeklarujesz statyczną składową danych w ramach definicji klasy jako **dllexport**, definicja musi znajdować się w tym samym programie (podobnie jak w przypadku zewnętrznego powiązania poza klasą).

Podobnie można zadeklarować funkcje członkowskie z atrybutami **dllimport** lub **dllexport** . W takim przypadku należy podać definicję **dllexport** w ramach tego samego programu.

Warto pamiętać o kilku istotnych kwestiach dotyczących selektywnego importu i eksportu elementu członkowskiego:

- Selektywny element członkowski importu/eksportu najlepiej nadaje się do dostarczania wersji interfejsu klasy wyeksportowanej, która jest bardziej restrykcyjna; czyli takiej, dla której można zaprojektować bibliotekę DLL, która udostępnia mniej funkcji publicznych i prywatnych, niż umożliwiłby to język w przeciwnym razie. Jest on również przydatny do precyzyjnego dostosowywania interfejsu, który można eksportować, gdy wiadomo, że klient, zgodnie z definicją, nie jest w stanie uzyskać dostępu do niektórych danych prywatnych; nie trzeba eksportować całej klasy.

- Podczas eksportowania jednej wirtualnej funkcji w klasie, musisz je wszystkie wyeksportować lub przynajmniej dostarczyć wersje, które klient może używać bezpośrednio.

- Jeśli posiadasz klasę, w której wykorzystujesz selektywny członkowski import/eksport z funkcjami wirtualnymi, funkcje muszą znajdować się w interfejsie, nadającym się do eksportu lub zdefiniowanej instrukcji inline (widoczne dla klienta).

- Jeśli element członkowski zostanie zdefiniowany jako **dllexport** , ale nie zostanie uwzględniony w definicji klasy, zostanie wygenerowany błąd kompilatora. Należy zdefiniować nagłówek dla elementu członkowskiego i klasy.

- Chociaż definicja elementów członkowskich klasy jako **dllimport** lub **dllexport** jest dozwolona, nie można zastąpić interfejsu określonego w definicji klasy.

- Jeśli zdefiniujesz funkcję członkowską w miejscu innym niż treść definicji klasy, w której została zadeklarowana, zostanie wygenerowane ostrzeżenie, jeśli funkcja jest zdefiniowana jako **dllexport** lub **dllimport** (Jeśli ta definicja różni się od określonej w deklaracji klasy).

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[dllexport, dllimport](../cpp/dllexport-dllimport.md)