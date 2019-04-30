---
title: Właściwości (C++/CX)
ms.date: 01/22/2017
ms.assetid: 64c7bc56-3191-4cd5-bdf4-476d07d285d5
ms.openlocfilehash: 8303952beefbbac13db14e148c6441c29a46b3d0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375226"
---
# <a name="properties-ccx"></a>Właściwości (C++/CX)

Typy środowiska wykonawczego Windows ujawnić dane publiczne jako właściwości. Kod klienta uzyskuje dostęp do właściwości, takich jak datamember publicznych. Wewnętrznie właściwość jest zaimplementowana jako blok, który zawiera metody dostępu get i/lub metody dostępu set. Za pomocą metody dostępu, można wykonywać dodatkowych czynności przed lub po pobraniu wartości, na przykład można wyzwolić zdarzenie lub wykonać sprawdzanie poprawności.

### <a name="remarks"></a>Uwagi

Wartość właściwości jest zawarta w zmiennej prywatnej — znane jako *magazyn zapasowy*— czyli tego samego typu, ponieważ właściwość. Właściwość może zawierać metody dostępu set, która przypisuje wartość do magazyn zapasowy, i metody dostępu get, który pobiera wartość magazyn zapasowy. Właściwość jest tylko do odczytu zawiera tylko akcesor pobierania, tylko do zapisu, jeśli zawiera tylko metody dostępu set i odczyt/zapis (można modyfikować) zapewnia obu metod dostępu.

A *trivial* właściwość jest właściwością odczytu/zapisu, dla których kompilator automatycznie implementuje metody dostępu i magazyn zapasowy. Nie masz dostępu do implementacji kompilatora. Jednak można zadeklarować właściwości niestandardowej i jawnie deklarować swoją metody dostępu i magazyn zapasowy. W ramach metodę dostępu możesz wykonać wszelka logika, która jest wymagana, takich jak sprawdzanie poprawności danych wejściowych do metody dostępu set, obliczania wartości z wartości właściwości, uzyskiwanie dostępu do bazy danych lub wyzwalanie zdarzeń, gdy właściwość.

Gdy C++tworzenia wystąpienia klasy ref /CX, jego pamięci jest inicjowany z wartością zerową przed jego konstruktor jest wywoływany; w związku z tym wszystkie właściwości są przypisywane domyślną wartość zero lub nullptr punkcie deklaracji.

### <a name="examples"></a>Przykłady

Poniższy przykład kodu pokazuje sposób deklarowania i dostępu do właściwości. Pierwszą właściwością `Name`, jest znany jako *trivial* właściwość, ponieważ kompilator automatycznie generuje `set` akcesora `get` metody dostępu i magazyn zapasowy.

Drugą właściwością `Doctor`, to właściwość tylko do odczytu, ponieważ określa on *blok właściwości* jawnie określa tylko `get` metody dostępu. Ponieważ jest zadeklarowany w bloku właściwości, należy jawnie zadeklarować magazyn zapasowy; oznacza to, że ciąg prywatnej ^ zmiennej `doctor_`. Zazwyczaj właściwość tylko do odczytu po prostu zwraca wartość magazyn zapasowy. Tylko klasy można ustawić wartość magazynie zapasowym, zazwyczaj w konstruktorze.

Właściwość trzeciej `Quantity`, jest właściwością odczytu i zapisu, ponieważ deklaruje bloku właściwości, która deklaruje zarówno `set` metody dostępu i `get` metody dostępu.

`set` Akcesor wykonuje test zdefiniowanych przez użytkownika ważność przypisaną wartością. W przeciwieństwie do języka C#, tutaj nazwę *wartość* tylko identyfikator parametr w to `set` akcesor; nie jest słowem kluczowym. Jeśli *wartość* nie jest większa niż zero, jest zgłaszany Platform::InvalidArgumentException. W przeciwnym razie przechowywania zapasowy `quantity_`, jest aktualizowany z przypisaną wartością.

Należy pamiętać, że na liście składowych nie można zainicjować właściwości. Oczywiście można zainicjować zmienne magazyn zapasowy na liście składowych.

[!code-cpp[cx_properties#01](../cppcx/codesnippet/CPP/cx_properties/class1.h#01)]

## <a name="see-also"></a>Zobacz także

[System typów](../cppcx/type-system-c-cx.md)<br/>
[Dokumentacja języka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Dokumentacja przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)
