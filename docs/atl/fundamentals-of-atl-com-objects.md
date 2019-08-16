---
title: Podstawowe informacje o obiektach COM ATL
ms.date: 11/19/2018
helpviewer_keywords:
- COM, and ATL
- ATL, COM
- ATL COM objects
- COM objects, ATL
ms.assetid: 0f9c9d98-cc28-45da-89ac-dc94cee422fe
ms.openlocfilehash: ec83539b2d7101c534bbc1df33577df422e76152
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492366"
---
# <a name="fundamentals-of-atl-com-objects"></a>Podstawowe informacje o obiektach COM ATL

Poniższa ilustracja przedstawia relację między klasami i interfejsami, które są używane do definiowania obiektu ATL COM.

![Struktura ATL](../atl/media/vc307y1.gif "Struktura ATL")

> [!NOTE]
>  Ten diagram pokazuje, `CComObject` że jest on `CYourClass` pochodną `CComPolyObject` `CComAggObject` i `CYourClass` zawiera jako zmienną członkowską.

Istnieją trzy sposoby definiowania obiektu ATL COM. Standardową opcją jest użycie `CComObject` klasy `CYourClass`pochodnej. Druga opcja polega na utworzeniu zagregowanego obiektu za pomocą `CComAggObject` klasy. Trzecią opcją jest użycie `CComPolyObject` klasy. `CComPolyObject`działa jako hybrydowe: może działać jako `CComObject` Klasa lub `CComAggObject` jako Klasa, w zależności od sposobu jej pierwszego utworzenia. Aby uzyskać więcej informacji o sposobach używania `CComPolyObject` klasy, zobacz [CComPolyObject class](../atl/reference/ccompolyobject-class.md).

W przypadku korzystania z standardowej biblioteki ATL COM, należy użyć dwóch obiektów: obiektu zewnętrznego i obiektu wewnętrznego. Klienci zewnętrzni uzyskują dostęp do funkcji obiektu wewnętrznego za pomocą funkcji otoki, które są zdefiniowane w obiekcie zewnętrznym. Obiekt zewnętrzny jest typu `CComObject`.

Gdy używasz obiektu zagregowanego, obiekt zewnętrzny nie zapewnia otoki dla funkcjonalności obiektu wewnętrznego. Zamiast tego obiekt zewnętrzny zawiera wskaźnik, do którego uzyskuje dostęp bezpośrednio przez klientów zewnętrznych. W tym scenariuszu obiektem zewnętrznym jest typ `CComAggObject`. Obiekt wewnętrzny jest zmienną członkowską obiektu zewnętrznego i jest typem `CYourClass`.

Ponieważ klient nie musi przechodzić przez zewnętrzny obiekt w celu współdziałania z obiektem wewnętrznym, zagregowane obiekty są zwykle bardziej wydajne. Ponadto obiekt zewnętrzny nie musi znać funkcjonalności obiektu zagregowanego, ponieważ interfejs zagregowanego obiektu jest bezpośrednio dostępny dla klienta. Jednak nie wszystkie obiekty mogą być agregowane. W przypadku obiektu, który ma zostać zagregowany, musi zostać zaprojektowany z uwzględnieniem agregacji.

ATL implementuje [interfejs IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) w dwóch fazach:

- [CComObject](../atl/reference/ccomobject-class.md), [CComAggObject](../atl/reference/ccomaggobject-class.md)lub [CComPolyObject](../atl/reference/ccompolyobject-class.md) implementuje `IUnknown` metody.

- [Klasy CComObjectRoot](../atl/reference/ccomobjectroot-class.md) lub [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) zarządza licznikiem odwołań i `IUnknown`zewnętrznymi wskaźnikami.

Inne aspekty obiektu COM ATL są obsługiwane przez inne klasy:

- [CComCoClass](../atl/reference/ccomcoclass-class.md) definiuje domyślną fabrykę klas i model agregacji obiektu.

- [IDispatchImpl](../atl/reference/idispatchimpl-class.md) zapewnia domyślną implementację `IDispatch Interface` części każdego podwójnego interfejsu w obiekcie.

- [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) implementuje `ISupportErrorInfo` interfejs, który zapewnia, że informacje o błędzie mogą być prawidłowo propagowane w łańcuchu wywołań.

## <a name="in-this-section"></a>W tej sekcji

[Implementowanie klasy CComObjectRootEx](../atl/implementing-ccomobjectrootex.md)<br/>
Pokaż przykładowe wpisy mapy COM do wdrożenia `CComObjectRootEx`.

[Implementowanie klas CComObject, CComAggObject i CComPolyObject](../atl/implementing-ccomobject-ccomaggobject-and-ccompolyobject.md)<br/>
Omawia, w jaki sposób makra **DECLARE_\*_AGGREGATABLE** wpływają na `CComObject`korzystanie `CComAggObject`z, `CComPolyObject`i.

[Obsługa interfejsów IDispatch i IErrorInfo](../atl/supporting-idispatch-and-ierrorinfo.md)<br/>
Wyświetla listę klas implementacji ATL, które mają być używane `IDispatch` do `IErrorInfo` obsługi interfejsów i.

[Obsługa interfejsu IDispEventImpl](../atl/supporting-idispeventimpl.md)<br/>
W tym artykule omówiono procedurę implementowania punktu połączenia dla klasy.

[Zmienianie domyślnej fabryki klas i modelu agregacji](../atl/changing-the-default-class-factory-and-aggregation-model.md)<br/>
Pokaż, które makra użyć do zmiany domyślnego fabryki klas i modelu agregacji.

[Tworzenie obiektu zagregowanego](../atl/creating-an-aggregated-object.md)<br/>
Wyświetla listę kroków tworzenia zagregowanego obiektu.

## <a name="related-sections"></a>Sekcje pokrewne

[Tworzenie projektu ATL](../atl/reference/creating-an-atl-project.md)<br/>
Zawiera informacje na temat tworzenia obiektu ATL COM.

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
Zawiera łącza do tematów koncepcyjnych dotyczących sposobu programowania przy użyciu Active Template Library.

## <a name="see-also"></a>Zobacz także

[Pojęcia](../atl/active-template-library-atl-concepts.md)
