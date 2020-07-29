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
ms.openlocfilehash: 4687db45c767f4323c97aff0a685aa3aeeb83e94
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227013"
---
# <a name="using-dllimport-and-dllexport-in-c-classes"></a>Korzystanie z dllimport i dllexport w klasach C++

**Specyficzne dla firmy Microsoft**

Można zadeklarować klasy C++ przy użyciu **`dllimport`** **`dllexport`** atrybutu lub. Te formularze oznaczają, że cała klasa jest importowana lub eksportowana. Klasy eksportowane w ten sposób są nazywane klasami możliwymi do eksportu.

W poniższym przykładzie zdefiniowano klasę, która ma zostać wyeksportowana. Wszystkie funkcje składowe i dane statyczne są eksportowane:

```cpp
#define DllExport   __declspec( dllexport )

class DllExport C {
   int i;
   virtual int func( void ) { return 1; }
};
```

Należy zauważyć, że jawne użycie **`dllimport`** **`dllexport`** atrybutów i dla elementów członkowskich klasy możliwej do eksportu jest zabronione.

## <a name="dllexport-classes"></a><a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bdllexportclasses"></a>Klasy dllexport

Podczas deklarowania klasy **`dllexport`** , wszystkie jej funkcje członkowskie i statyczne składowe danych są eksportowane. Należy podać definicje wszystkich takich członków w tym samym programie. W przeciwnym razie zostanie wygenerowany błąd konsolidatora. Jedynym wyjątkiem od tej reguły są odnoszące się do czystych funkcji wirtualnych, dla których nie trzeba podawać jawnych definicji. Jednak ponieważ destruktor klasy abstrakcyjnej jest zawsze wywoływany przez destruktor dla klasy bazowej, czyste destruktory wirtualne muszą zawsze podawać definicję. Należy zauważyć, że te reguły są takie same dla klas nieprzeznaczonych do eksportu.

W przypadku eksportowania danych typu klasy lub funkcji, które zwracają klasy, należy wyeksportować klasę.

## <a name="dllimport-classes"></a><a name="_pluslang_dllexport_classesdllexportclasses"></a>Klasy dllimport

Podczas deklarowania klasy **`dllimport`** , wszystkie jej funkcje członkowskie i statyczne składowe danych są importowane. W przeciwieństwie do zachowania **`dllimport`** i **`dllexport`** w typach nieklas, statyczne składowe danych nie mogą określać definicji w tym samym programie, w którym **`dllimport`** zdefiniowano klasę.

## <a name="inheritance-and-exportable-classes"></a><a name="_pluslang_using_dllimport_and_dllexport_in_c2b2binheritanceandexportableclasses"></a>Dziedziczenie i możliwe do eksportowania klasy

Wszystkie klasy bazowe klasy możliwej do eksportu muszą być eksportowane. Jeśli nie, generowane jest ostrzeżenie kompilatora. Ponadto wszystkie dostępne elementy członkowskie, które są również klasami, muszą być eksportowane. Ta reguła zezwala **`dllexport`** klasie na dziedziczenie z **`dllimport`** klasy, a Klasa, **`dllimport`** która ma dziedziczyć z **`dllexport`** klasy (mimo że nie jest to zalecane). Zgodnie z regułą wszystko, co jest dostępne dla klienta biblioteki DLL (zgodnie z regułami dostępu języka C++), musi być częścią interfejsu, który można eksportować. Obejmuje to prywatne składowe danych, do których istnieją odwołania w funkcjach wbudowanych.

## <a name="selective-member-importexport"></a><a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bselectivememberimportexport"></a>Selektywny element członkowski importu/eksportu

Ponieważ funkcje składowe i dane statyczne w klasie niejawnie mają powiązania zewnętrzne, można je zadeklarować przy użyciu **`dllimport`** **`dllexport`** atrybutu lub, chyba że cała klasa zostanie wyeksportowana. Jeśli cała klasa została zaimportowana lub wyeksportowana, jawna deklaracja funkcji składowych i danych **`dllimport`** **`dllexport`** jest zabroniona. Jeśli zadeklarujesz statyczną składową danych w ramach definicji klasy jako **`dllexport`** , definicja musi znajdować się w tym samym programie (podobnie jak w przypadku zewnętrznego powiązania poza klasą).

Podobnie można zadeklarować funkcje członkowskie z **`dllimport`** **`dllexport`** atrybutami lub. W takim przypadku należy podać **`dllexport`** definicję w ramach tego samego programu.

Należy pamiętać o kilku ważnych kwestiach dotyczących importu i eksportu członków selektywnych:

- Selektywny import/eksport składowej najlepiej służy do udostępniania wersji wyeksportowanego interfejsu klasy, który jest bardziej restrykcyjny; oznacza to, że można zaprojektować bibliotekę DLL, która udostępnia mniejszą liczbę funkcji publicznych i prywatnych, niż język dozwolony w inny sposób. Jest on również przydatny do precyzyjnego dostrajania interfejsu, który można eksportować: gdy wiadomo, że klient, zgodnie z definicją, nie jest w stanie uzyskać dostępu do niektórych danych prywatnych, nie trzeba eksportować całej klasy.

- W przypadku eksportowania jednej funkcji wirtualnej w klasie należy wyeksportować wszystkie z nich lub co najmniej wersje, które mogą być używane przez klienta bezpośrednio.

- Jeśli masz klasę, w której używasz selektywnego importu/eksportu elementu członkowskiego z funkcjami wirtualnymi, funkcje muszą znajdować się w interfejsie możliwym do eksportu lub zdefiniowane w tekście (widoczne dla klienta).

- W przypadku zdefiniowania elementu członkowskiego, jeśli **`dllexport`** nie zostanie on uwzględniony w definicji klasy, zostanie wygenerowany błąd kompilatora. Należy zdefiniować element członkowski w nagłówku klasy.

- Chociaż definicje składowych klasy **`dllimport`** **`dllexport`** są dozwolone, nie można zastąpić interfejsu określonego w definicji klasy.

- Jeśli zdefiniujesz funkcję członkowską w miejscu innym niż treść definicji klasy, w której została zadeklarowana, ostrzeżenie jest generowane, jeśli funkcja jest zdefiniowana jako **`dllexport`** lub **`dllimport`** (Jeśli ta definicja różni się od określonej w deklaracji klasy).

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[dllexport, dllimport](../cpp/dllexport-dllimport.md)
