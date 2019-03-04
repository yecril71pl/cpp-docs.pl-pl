---
title: Podstawowe informacje na temat obiektów COM ATL
ms.date: 11/19/2018
helpviewer_keywords:
- COM, and ATL
- ATL, COM
- ATL COM objects
- COM objects, ATL
ms.assetid: 0f9c9d98-cc28-45da-89ac-dc94cee422fe
ms.openlocfilehash: cba26ede01b69e4a077f1e842982adc8c2127331
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57270049"
---
# <a name="fundamentals-of-atl-com-objects"></a>Podstawowe informacje na temat obiektów COM ATL

Poniższa ilustracja przedstawia relacje między klasy i interfejsy, które są używane do zdefiniowania obiektu ATL COM.

![Struktura ATL](../atl/media/vc307y1.gif "struktury ATL")

> [!NOTE]
>  Ten diagram pokazuje, że `CComObject` jest tworzony na podstawie `CYourClass` natomiast `CComAggObject` i `CComPolyObject` obejmują `CYourClass` jako zmienną składową.

Istnieją trzy sposoby, aby zdefiniować obiekt ATL COM. Standardowa opcją jest użycie `CComObject` klasę, która jest pochodną `CYourClass`. Drugą opcją jest tworzenie obiektu zagregowanego za pomocą `CComAggObject` klasy. Trzecia opcja jest użycie `CComPolyObject` klasy. `CComPolyObject` działa jako hybrydowego: może działać jako `CComObject` klasy lub jako `CComAggObject` klasy, w zależności od tego, jak jej pierwszego tworzenia. Aby uzyskać więcej informacji o sposobie używania `CComPolyObject` klasy, zobacz [klasa CComPolyObject](../atl/reference/ccompolyobject-class.md).

Użycie opcji standard ATL COM, użyj dwóch obiektów: Obiekt wewnętrzny i zewnętrzny obiektu. Klienci zewnętrzni uzyskać dostęp do funkcji wewnętrznego obiektu za pomocą funkcji otoki, które są zdefiniowane w obiekcie zewnętrznym. Typ obiektu zewnętrznego to `CComObject`.

Korzystając z obiektu zagregowanego obiektu zewnętrznego nie zapewnia otoki dla funkcji obiektu wewnętrznego. Zamiast tego obiektu zewnętrznego zapewnia wskaźnika, który jest bezpośrednio dostępny dla klientów zewnętrznych. W tym scenariuszu obiektu zewnętrznego jest typu `CComAggObject`. Obiekt wewnętrzny jest zmienną elementu członkowskiego obiektu zewnętrznego i jest typu `CYourClass`.

Ponieważ klient nie ma za pośrednictwem obiektu zewnętrznego do interakcji z obiekt wewnętrzny, zagregowane obiekty są zwykle bardziej wydajne. Ponadto obiektu zewnętrznego nie ma znać funkcje obiektu zagregowane, biorąc pod uwagę, że interfejs obiektu zagregowanego jest dostępne bezpośrednio do klienta. Jednak nie wszystkie obiekty mogą być agregowane. Dla obiektu agregowania musi ona być zaprojektowane tak, za pomocą agregacji, należy pamiętać.

Implementuje ATL [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) w dwóch fazach:

- [CComObject](../atl/reference/ccomobject-class.md), [CComAggObject](../atl/reference/ccomaggobject-class.md), lub [CComPolyObject](../atl/reference/ccompolyobject-class.md) implementuje `IUnknown` metody.

- [CComObjectRoot](../atl/reference/ccomobjectroot-class.md) lub [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) zarządza licznika odwołań i zewnętrznych wskaźników `IUnknown`.

Inne aspekty obiekt ATL COM są obsługiwane przez inne klasy:

- [Klasy CComCoClass](../atl/reference/ccomcoclass-class.md) definiuje obiektu domyślnej klasy fabryki i agregację modelu.

- [IDispatchImpl](../atl/reference/idispatchimpl-class.md) udostępnia domyślną implementację elementu `IDispatch Interface` część wszelkie dwa interfejsy do obiektu.

- [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) implementuje `ISupportErrorInfo` interfejsu, która zapewnia informacje o błędzie mogą być przekazywane łańcuch wywołań poprawnie.

## <a name="in-this-section"></a>W tej sekcji

[Implementowanie klasy CComObjectRootEx](../atl/implementing-ccomobjectrootex.md)<br/>
Pokaż przykład wpisy mapy modelu COM do implementowania `CComObjectRootEx`.

[Implementowanie klas CComObject, CComAggObject i CComPolyObject](../atl/implementing-ccomobject-ccomaggobject-and-ccompolyobject.md)<br/>
W tym artykule omówiono sposób, w jaki **DECLARE_\*_AGGREGATABLE** makra wpływa na użycie `CComObject`, `CComAggObject`, i `CComPolyObject`.

[Obsługa interfejsów IDispatch i IErrorInfo](../atl/supporting-idispatch-and-ierrorinfo.md)<br/>
Wyświetla listę klas ATL wdrażania służące do obsługi `IDispatch` i `IErrorInfo` interfejsów.

[Obsługa interfejsu IDispEventImpl](../atl/supporting-idispeventimpl.md)<br/>
W tym artykule omówiono kroki, aby wdrożyć punkt połączenia dla swojej klasy.

[Zmienianie domyślnej fabryki klas i modelu agregacji](../atl/changing-the-default-class-factory-and-aggregation-model.md)<br/>
Pokaż makra, jakie można użyć, aby zmienić model fabryki i agregację klasy domyślne.

[Tworzenie obiektu zagregowanego](../atl/creating-an-aggregated-object.md)<br/>
Lista czynności prowadzących do tworzenie obiektu zagregowanego.

## <a name="related-sections"></a>Sekcje pokrewne

[Tworzenie projektu ATL](../atl/reference/creating-an-atl-project.md)<br/>
Zawiera informacje dotyczące tworzenia obiektu ATL COM.

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
Zawiera łącza do tematów pojęciowych dotyczące programowania przy użyciu biblioteki Active Template Library.

## <a name="see-also"></a>Zobacz także

[Pojęcia](../atl/active-template-library-atl-concepts.md)
