---
title: Właściwości (C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 64c7bc56-3191-4cd5-bdf4-476d07d285d5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f5cfe1bf4ae614bc892b4ea93d36fa44604029f1
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42600858"
---
# <a name="properties-ccx"></a>Właściwości (C + +/ CX)
Typy środowiska wykonawczego Windows ujawnić dane publiczne jako właściwości. Kod klienta uzyskuje dostęp do właściwości, takich jak datamember publicznych. Wewnętrznie właściwość jest zaimplementowana jako blok, który zawiera metody dostępu get i/lub metody dostępu set. Za pomocą metody dostępu, można wykonywać dodatkowych czynności przed lub po pobraniu wartości, na przykład można wyzwolić zdarzenie lub wykonać sprawdzanie poprawności.  
  
### <a name="remarks"></a>Uwagi  
 Wartość właściwości jest zawarta w zmiennej prywatnej — znane jako *magazyn zapasowy*— czyli tego samego typu, ponieważ właściwość. Właściwość może zawierać metody dostępu set, która przypisuje wartość do magazyn zapasowy, i metody dostępu get, który pobiera wartość magazyn zapasowy. Właściwość jest tylko do odczytu zawiera tylko akcesor pobierania, tylko do zapisu, jeśli zawiera tylko metody dostępu set i odczyt/zapis (można modyfikować) zapewnia obu metod dostępu.  
  
 A *trivial* właściwość jest właściwością odczytu/zapisu, dla których kompilator automatycznie implementuje metody dostępu i magazyn zapasowy. Nie masz dostępu do implementacji kompilatora. Jednak można zadeklarować właściwości niestandardowej i jawnie deklarować swoją metody dostępu i magazyn zapasowy. W ramach metodę dostępu możesz wykonać wszelka logika, która jest wymagana, takich jak sprawdzanie poprawności danych wejściowych do metody dostępu set, obliczania wartości z wartości właściwości, uzyskiwanie dostępu do bazy danych lub wyzwalanie zdarzeń, gdy właściwość.  
  
 Gdy w języku C + +/ CX klasy referencyjnej zostanie uruchomiony, jego pamięci jest inicjowany z wartością zerową przed jego konstruktor jest wywoływana w związku z tym wszystkie właściwości są przypisywane domyślną wartość zero lub nullptr punkcie deklaracji.  
  
### <a name="examples"></a>Przykłady  
 Poniższy przykład kodu pokazuje sposób deklarowania i dostępu do właściwości. Pierwszą właściwością `Name`, jest znany jako *trivial* właściwość, ponieważ kompilator automatycznie generuje `set` akcesora `get` metody dostępu i magazyn zapasowy.  
  
 Drugą właściwością `Doctor`, to właściwość tylko do odczytu, ponieważ określa on *blok właściwości* jawnie określa tylko `get` metody dostępu. Ponieważ jest zadeklarowany w bloku właściwości, należy jawnie zadeklarować magazyn zapasowy; oznacza to, że ciąg prywatnej ^ zmiennej `doctor_`. Zazwyczaj właściwość tylko do odczytu po prostu zwraca wartość magazyn zapasowy. Tylko klasy można ustawić wartość magazynie zapasowym, zazwyczaj w konstruktorze.  
  
 Właściwość trzeciej `Quantity`, jest właściwością odczytu i zapisu, ponieważ deklaruje bloku właściwości, która deklaruje zarówno `set` metody dostępu i `get` metody dostępu.  
  
 `set` Akcesor wykonuje test zdefiniowanych przez użytkownika ważność przypisaną wartością. W przeciwieństwie do języka C#, tutaj nazwę *wartość* tylko identyfikator parametr w to `set` akcesor; nie jest słowem kluczowym. Jeśli *wartość* nie jest większa niż zero, jest zgłaszany Platform::InvalidArgumentException. W przeciwnym razie przechowywania zapasowy `quantity_`, jest aktualizowany z przypisaną wartością.  
  
 Należy pamiętać, że na liście składowych nie można zainicjować właściwości. Oczywiście można zainicjować zmienne magazyn zapasowy na liście składowych.  
  
 [!code-cpp[cx_properties#01](../cppcx/codesnippet/CPP/cx_properties/class1.h#01)]  
  
## <a name="see-also"></a>Zobacz też  
 [System typów](../cppcx/type-system-c-cx.md)   
 [Dokumentacja języka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Odwołanie do przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)