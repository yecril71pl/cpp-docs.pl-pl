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
ms.openlocfilehash: c0a2c96a37f58c956976980beafd5ecbed4d1318
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365115"
---
# <a name="using-dllimport-and-dllexport-in-c-classes"></a>Korzystanie z dllimport i dllexport w klasach C++

**Specyficzne dla firmy Microsoft**

Można zadeklarować klasy C++ z **atrybutem dllimport** lub **dllexport.** Formularze te oznaczają, że cała klasa jest importowana lub eksportowana. Klasy eksportowane w ten sposób są nazywane klasami eksportowalnymi.

Poniższy przykład definiuje klasę eksportowalną. Eksportowane są wszystkie funkcje członkowskie i dane statyczne:

```cpp
#define DllExport   __declspec( dllexport )

class DllExport C {
   int i;
   virtual int func( void ) { return 1; }
};
```

Należy zauważyć, że jawne użycie atrybutów **dllimport** i **dllexport** na elementach członkowskich klasy eksportowania jest zabronione.

## <a name="dllexport-classes"></a><a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bdllexportclasses"></a>Klasy dllexport

Podczas deklarowania **dllexport**klasy, wszystkie jego funkcje członkowskie i elementy członkowskie danych statycznych są eksportowane. Należy podać definicje wszystkich takich członków w tym samym programie. W przeciwnym razie generowany jest błąd konsolidatora. Jedyny wyjątek od tej reguły ma zastosowanie do czystych funkcji wirtualnych, dla których nie trzeba podawać jawnych definicji. Jednak ponieważ destruktor dla klasy abstrakcyjnej jest zawsze wywoływany przez destruktora dla klasy podstawowej, czyste destruktory wirtualne zawsze muszą zawierać definicję. Należy zauważyć, że te reguły są takie same dla klas nieeksportowalnych.

Jeśli eksportujesz dane typu klasy lub funkcje, które zwracają klasy, należy wyeksportować klasę.

## <a name="dllimport-classes"></a><a name="_pluslang_dllexport_classesdllexportclasses"></a>Klasy dllimport

Podczas deklarowania **dllimport**klasy, wszystkie jego funkcje członkowskie i elementy członkowskie danych statycznych są importowane. W przeciwieństwie do zachowania **dllimport** i **dllexport** na typach innych niżclass, statyczne elementy członkowskie danych nie można określić definicji w tym samym programie, w którym klasa **dllimport** jest zdefiniowana.

## <a name="inheritance-and-exportable-classes"></a><a name="_pluslang_using_dllimport_and_dllexport_in_c2b2binheritanceandexportableclasses"></a>Klasy dziedziczenia i eksportu

Wszystkie klasy podstawowe klasy eksportowalnej muszą być eksportowane. Jeśli nie, generowane jest ostrzeżenie kompilatora. Ponadto wszystkie dostępne elementy członkowskie, które są również klasy muszą być eksportowane. Ta reguła zezwala **dllexport** klasy dziedziczyć z **dllimport** klasy i **dllimport** klasy dziedziczyć z **dllexport** klasy (choć ten ostatni nie jest zalecane). Z reguły wszystko, co jest dostępne dla klienta biblioteki DLL (zgodnie z regułami dostępu C++) powinno być częścią interfejsu eksportującego. Obejmuje to prywatne elementy członkowskie danych, do których odwołuje się wbudowane funkcje.

## <a name="selective-member-importexport"></a><a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bselectivememberimportexport"></a>Selektywny element członkowski Import/Eksport

Ponieważ funkcje członkowskie i dane statyczne w klasie niejawnie mają powiązania zewnętrznego, można zadeklarować je za pomocą **atrybutu dllimport** lub **dllexport,** chyba że cała klasa jest eksportowana. Jeśli cała klasa jest importowana lub eksportowana, jawna deklaracja funkcji elementów członkowskich i danych jako **dllimport** lub **dllexport** jest zabroniona. Jeśli deklarujesz element członkowski danych statycznych w definicji klasy jako **dllexport,** definicja musi wystąpić gdzieś w ramach tego samego programu (jak w przypadku powiązania zewnętrznego nonclass).

Podobnie można zadeklarować funkcje członkowskie za pomocą atrybutów **dllimport** lub **dllexport.** W takim przypadku należy podać definicję **dllexport** gdzieś w ramach tego samego programu.

Warto zwrócić uwagę na kilka ważnych kwestii dotyczących selektywnego importu i eksportu członków:

- Selektywny element członkowski import/eksport jest najlepiej używany do dostarczania wersji wyeksportowanego interfejsu klasy, która jest bardziej restrykcyjna; oznacza to, że jeden, dla którego można zaprojektować bibliotekę DLL, która udostępnia mniej funkcji publicznych i prywatnych niż język w przeciwnym razie pozwoli. Jest to również przydatne do dostrajania eksportowania interfejsu: gdy wiadomo, że klient z definicji nie może uzyskać dostępu do niektórych prywatnych danych, nie musisz eksportować całej klasy.

- Jeśli eksportujesz jedną funkcję wirtualną w klasie, należy wyeksportować wszystkie z nich lub przynajmniej podać wersje, których klient może używać bezpośrednio.

- Jeśli masz klasę, w której używasz selektywnego importu/eksportu elementu członkowskiego z funkcjami wirtualnymi, funkcje muszą znajdować się w interfejsie eksportowalnym lub zdefiniowanym wbudowanym (widocznym dla klienta).

- Jeśli definiujesz element członkowski jako **dllexport,** ale nie uwzględniasz go w definicji klasy, generowany jest błąd kompilatora. Należy zdefiniować element członkowski w nagłówku klasy.

- Chociaż definicja członków klasy jako **dllimport** lub **dllexport** jest dozwolona, nie można zastąpić interfejsu określonego w definicji klasy.

- Jeśli definiujesz funkcję elementu członkowskiego w miejscu innym niż treść definicji klasy, w którym została zadeklarowana, ostrzeżenie jest generowane, jeśli funkcja jest zdefiniowana jako **dllexport** lub **dllimport** (jeśli ta definicja różni się od tej określonej w deklaracji klasy).

**ZAKOŃCZ Specyficzne dla firmy Microsoft**

## <a name="see-also"></a>Zobacz też

[dllexport, dllimport](../cpp/dllexport-dllimport.md)
