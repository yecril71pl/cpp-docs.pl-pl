---
title: Właściwości (C++/CX)
ms.date: 01/22/2017
ms.assetid: 64c7bc56-3191-4cd5-bdf4-476d07d285d5
ms.openlocfilehash: fdff2bf5abd3177eda962b7cc55ace1078522f32
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741093"
---
# <a name="properties-ccx"></a>Właściwości (C++/CX)

Typy środowisko wykonawcze systemu Windows uwidaczniają dane publiczne jako właściwości. Kod klienta uzyskuje dostęp do właściwości, takiej jak publiczny element członkowski. Wewnętrznie właściwość jest implementowana jako blok, który zawiera metodę get akcesora, metodę dostępu set lub obie. Przy użyciu metod dostępu można wykonać dodatkowe akcje przed lub po pobraniu wartości, na przykład, można wywołać zdarzenie lub przeprowadzić testy weryfikacyjne.

### <a name="remarks"></a>Uwagi

Wartość właściwości jest zawarta w zmiennej prywatnej — nazywanej *magazynem zapasowym*, który jest taki sam jak typ właściwości. Właściwość może zawierać zarówno metodę dostępu zestawu, która przypisuje wartość do magazynu zapasowego, jak i metodę dostępu get, która pobiera wartość magazynu zapasowego. Właściwość jest tylko do odczytu, jeśli zawiera tylko metodę dostępu get, tylko do zapisu, jeśli zawiera tylko metodę dostępu set i odczyt/zapis (modyfikowalny), jeśli zapewnia obydwie metody dostępu.

*Prosta* właściwość jest właściwością do odczytu/zapisu, dla której kompilator automatycznie implementuje metody dostępu i magazyn zapasowy. Nie masz dostępu do implementacji kompilatora. Można jednak zadeklarować właściwość niestandardową i jawnie zadeklarować jej metody dostępu i magazyn zapasowy. W ramach metody dostępu można wykonać dowolną wymaganą logikę, taką jak walidacja danych wejściowych do zestawu akcesora, obliczanie wartości z wartości właściwości, uzyskiwanie dostępu do bazy danych lub Wyzwalanie zdarzenia po zmianie właściwości.

Po utworzeniu C++wystąpienia klasy ref/CX jej pamięć jest inicjowana zero przed wywołaniem konstruktora; w związku z tym wszystkie właściwości są przypisywane wartości domyślnej zero lub nullptr w punkcie deklaracji.

### <a name="examples"></a>Przykłady

Poniższy przykład kodu pokazuje, jak zadeklarować Właściwość i uzyskać do niej dostęp. Pierwsza Właściwość `Name`,,, jest znana jako właściwość *prosta* , ponieważ `set` kompilator automatycznie generuje metodę dostępu, `get` akcesor i magazyn zapasowy.

Druga właściwość,, `Doctor`jest właściwością tylko do odczytu, ponieważ określa *blok właściwości* , który `get` jawnie deklaruje tylko metodę dostępu. Ponieważ blok właściwości jest zadeklarowany, należy jawnie zadeklarować magazyn zapasowy; oznacza to, że jest to zmienna `doctor_`ciągu prywatnego ^. Zazwyczaj właściwość tylko do odczytu zwraca wartość magazynu zapasowego. Tylko sama klasa może ustawić wartość magazynu zapasowego, zazwyczaj w konstruktorze.

Trzecia Właściwość `Quantity`,, jest właściwością do odczytu i zapisu, ponieważ deklaruje blok właściwości, który deklaruje `set` metodę dostępu i `get` akcesor.

`set` Metoda dostępu wykonuje test ważności zdefiniowany przez użytkownika dla przypisanej wartości. I w przeciwieństwie C#do tego, *wartość* nazwy jest tylko identyfikatorem `set` parametru w metodzie dostępu; nie jest to słowo kluczowe. Jeśli *wartość* nie jest większa od zera, zgłaszany jest obiekt platform:: InvalidArgumentException. W przeciwnym razie magazyn `quantity_`zapasowy, jest aktualizowany przy użyciu przypisanej wartości.

Należy zauważyć, że właściwość nie może zostać zainicjowana na liście elementów członkowskich. Możesz inicjować na liście elementów członkowskich zmienne magazynu zapasowego.

[!code-cpp[cx_properties#01](../cppcx/codesnippet/CPP/cx_properties/class1.h#01)]

## <a name="see-also"></a>Zobacz także

[System typów](../cppcx/type-system-c-cx.md)<br/>
[Dokumentacja języka C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Dokumentacja przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)
