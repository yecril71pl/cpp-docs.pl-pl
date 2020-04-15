---
title: Podstawy obiektów ATL COM
ms.date: 11/19/2018
helpviewer_keywords:
- COM, and ATL
- ATL, COM
- ATL COM objects
- COM objects, ATL
ms.assetid: 0f9c9d98-cc28-45da-89ac-dc94cee422fe
ms.openlocfilehash: 651413534ed44143e2a0fdaf00bdabd6e5d57010
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319555"
---
# <a name="fundamentals-of-atl-com-objects"></a>Podstawy obiektów ATL COM

Na poniższej ilustracji przedstawiono relację między klasami i interfejsami, które są używane do definiowania obiektu ATL COM.

![Struktura ATL](../atl/media/vc307y1.gif "Struktura ATL")

> [!NOTE]
> Ten diagram `CComObject` pokazuje, że `CYourClass` pochodzi `CComAggObject` `CComPolyObject` od `CYourClass` natomiast i obejmują jako zmiennej elementu członkowskiego.

Istnieją trzy sposoby definiowania obiektu ATL COM. Standardową opcją jest `CComObject` użycie klasy, która `CYourClass`pochodzi od . Drugą opcją jest utworzenie obiektu zagregowanego przy użyciu `CComAggObject` klasy. Trzecią opcją jest użycie `CComPolyObject` klasy. `CComPolyObject`działa jako hybryda: może `CComObject` działać jako `CComAggObject` klasa lub jako klasa, w zależności od tego, jak jest tworzony po raz pierwszy. Aby uzyskać więcej informacji `CComPolyObject` na temat korzystania z klasy, zobacz [CComPolyObject Class](../atl/reference/ccompolyobject-class.md).

Korzystając ze standardowego atl com, należy użyć dwóch obiektów: obiektu zewnętrznego i obiektu wewnętrznego. Klienci zewnętrzni uzyskują dostęp do funkcji obiektu wewnętrznego za pośrednictwem funkcji otoki zdefiniowanych w obiekcie zewnętrznym. Obiekt zewnętrzny jest `CComObject`typu .

W przypadku korzystania z obiektu zagregowanego obiekt zewnętrzny nie zapewnia otoki dla funkcjonalności obiektu wewnętrznego. Zamiast tego obiekt zewnętrzny udostępnia wskaźnik, który jest bezpośrednio dostępny dla klientów zewnętrznych. W tym scenariuszu obiekt zewnętrzny jest typu `CComAggObject`. Obiekt wewnętrzny jest zmienną elementu członkowskiego obiektu zewnętrznego `CYourClass`i jest typem.

Ponieważ klient nie musi przechodzić przez obiekt zewnętrzny do interakcji z obiektem wewnętrznym, zagregowane obiekty są zwykle bardziej wydajne. Ponadto obiekt zewnętrzny nie musi znać funkcjonalność zagregowanego obiektu, biorąc pod uwagę, że interfejs zagregowanego obiektu jest bezpośrednio dostępny dla klienta. Jednak nie wszystkie obiekty mogą być agregowane. Aby obiekt został zagregowany, musi być zaprojektowany z myślą o agregacji.

ATL implementuje [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) w dwóch etapach:

- [CComObject](../atl/reference/ccomobject-class.md), [CComAggObject](../atl/reference/ccomaggobject-class.md)lub [CComPolyObject](../atl/reference/ccompolyobject-class.md) implementuje `IUnknown` metody.

- [CComObjectRoot](../atl/reference/ccomobjectroot-class.md) lub [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) zarządza liczbą odwołań `IUnknown`i zewnętrznymi wskaźnikami .

Inne aspekty obiektu ATL COM są obsługiwane przez inne klasy:

- [CComCoClass](../atl/reference/ccomcoclass-class.md) definiuje domyślną fabrykę klasy obiektu i model agregacji.

- [IDispatchImpl](../atl/reference/idispatchimpl-class.md) zapewnia domyślną `IDispatch Interface` implementację części dowolnego podwójnego interfejsu na obiekcie.

- [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) implementuje `ISupportErrorInfo` interfejs, który zapewnia, że informacje o błędzie mogą być propagowane w górę łańcucha wywołań poprawnie.

## <a name="in-this-section"></a>W tej sekcji

[Implementowanie klasy CComObjectRootEx](../atl/implementing-ccomobjectrootex.md)<br/>
Pokaż przykładowe wpisy mapy `CComObjectRootEx`COM do zaimplementowania .

[Implementowanie klas CComObject, CComAggObject i CComPolyObject](../atl/implementing-ccomobject-ccomaggobject-and-ccompolyobject.md)<br/>
W tym artykule omówiono, w jaki sposób DECLARE_ `CComObject` `CComAggObject` **\*_AGGREGATABLE** `CComPolyObject`makra wpływają na użycie programów , i .

[Obsługa interfejsów IDispatch i IErrorInfo](../atl/supporting-idispatch-and-ierrorinfo.md)<br/>
Wyświetla listę klas implementacji ATL `IDispatch` do `IErrorInfo` użycia do obsługi interfejsów i interfejsów.

[Obsługa interfejsu IDispEventImpl](../atl/supporting-idispeventimpl.md)<br/>
W tym artykule omówiono kroki, aby zaimplementować punkt połączenia dla klasy.

[Zmiana domyślnego modelu fabryki i agregacji klasy](../atl/changing-the-default-class-factory-and-aggregation-model.md)<br/>
Pokaż, jakich makr użyć do zmiany domyślnej fabryki klasy i modelu agregacji.

[Tworzenie obiektu zagregowanego](../atl/creating-an-aggregated-object.md)<br/>
Wyświetla listę kroków tworzenia obiektu zagregowanego.

## <a name="related-sections"></a>Sekcje pokrewne

[Tworzenie projektu ATL](../atl/reference/creating-an-atl-project.md)<br/>
Zawiera informacje dotyczące tworzenia obiektu ATL COM.

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
Zawiera łącza do tematów koncepcyjnych dotyczących programowania przy użyciu aktywnej biblioteki szablonów.

## <a name="see-also"></a>Zobacz też

[Pojęcia](../atl/active-template-library-atl-concepts.md)
