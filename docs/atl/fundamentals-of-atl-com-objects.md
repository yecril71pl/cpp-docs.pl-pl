---
title: Podstawowe informacje dotyczące obiektów COM ATL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- COM, and ATL
- ATL, COM
- ATL COM objects
- COM objects, ATL
ms.assetid: 0f9c9d98-cc28-45da-89ac-dc94cee422fe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 955f8f6be96feeaf0f22f02c125dcdeaceb8e7f8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="fundamentals-of-atl-com-objects"></a>Podstawowe informacje na temat ATL COM — obiekty
Na poniższej ilustracji przedstawiono relacje między klasy i interfejsy, które są używane do definiowania obiekt ATL COM.  
  
 ![Struktura ATL](../atl/media/vc307y1.gif "vc307y1")  
  
> [!NOTE]
>  Ten diagram przedstawia który `CComObject` jest pochodną `CYourClass` natomiast `CComAggObject` i `CComPolyObject` obejmują `CYourClass` jako zmienną członkowską.  
  
 Istnieją trzy sposoby próba zdefiniowania obiektu ATL COM. Standardowa opcja polega na `CComObject` klasy, która jest pochodną `CYourClass`. Drugą opcją jest do utworzenia obiektu zagregowane za pomocą `CComAggObject` klasy. Trzecia opcja jest użycie `CComPolyObject` klasy. `CComPolyObject` zachowuje się jak hybrydowego: może działać jako `CComObject` klasy lub jako `CComAggObject` klasy, w zależności od tego, jak jej pierwszego tworzenia. Aby uzyskać więcej informacji o sposobie używania `CComPolyObject` , zobacz [CComPolyObject klasy](../atl/reference/ccompolyobject-class.md).  
  
 Użycie standardowych ATL COM, użyj dwóch obiektów: Obiekt wewnętrzny i zewnętrzny obiektu. Zewnętrzne klienci uzyskują dostęp do funkcji Obiekt wewnętrzny za pośrednictwem funkcji otoki, które są zdefiniowane w obiekcie zewnętrznym. Zewnętrzny obiekt jest typu `CComObject`.  
  
 Korzystając z obiektu zagregowane, zewnętrzny obiekt nie ma otoki dla funkcji wewnętrzny obiekt. Zamiast tego obiektu zewnętrznego dostarcza wskaźnik, który jest bezpośrednio dostępny dla klientów zewnętrznych. W tym scenariuszu zewnętrzna obiekt jest typu `CComAggObject`. Wewnętrzny obiekt jest zmienną członkowską zewnętrznego obiektu i typu `CYourClass`.  
  
 Ponieważ klient nie musi przechodzić przez zewnętrznego obiektu wchodzić w interakcje z wewnętrzny obiekt, zagregowane obiekty są zwykle wydajniejszym. Ponadto zewnętrzny obiekt nie ma znać funkcje obiektu zagregowane, biorąc pod uwagę, że interfejs zagregowane obiektu jest bezpośrednio dostępny do klienta. Jednak nie wszystkie obiekty można agregowane. Dla obiekt agregowane musi zostać zaprojektowana z agregacją pamiętać.  
  
 Implementuje ATL [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) w dwóch fazach:  
  
-   [Element CComObject](../atl/reference/ccomobject-class.md), [CComAggObject](../atl/reference/ccomaggobject-class.md), lub [CComPolyObject](../atl/reference/ccompolyobject-class.md) implementuje **IUnknown** metody.  
  
-   [CComObjectRoot](../atl/reference/ccomobjectroot-class.md) lub [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) zarządza liczebności referencyjnej i zewnętrzne wskaźniki **IUnknown**.  
  
 Innych aspektów obiekt ATL COM są obsługiwane przez inne klasy:  
  
-   [Klasy CComCoClass](../atl/reference/ccomcoclass-class.md) definiuje obiektu domyślnej klasy fabryki i agregację modelu.  
  
-   [Elementem IDispatchImpl](../atl/reference/idispatchimpl-class.md) udostępnia domyślną implementację elementu `IDispatch Interface` część interfejsami podwójną obiektu.  
  
-   [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) implementuje **ISupportErrorInfo** interfejsu, który zapewnia informacje o błędzie mogą być poprawnie propagowane zapasowej łańcuch wywołań.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Implementowanie klasy CComObjectRootEx](../atl/implementing-ccomobjectrootex.md)  
 Pokaż przykład COM wpisy mapy implementacji `CComObjectRootEx`.  
  
 [Implementowanie klas CComObject, CComAggObject i CComPolyObject](../atl/implementing-ccomobject-ccomaggobject-and-ccompolyobject.md)  
 W tym artykule omówiono sposób **DECLARE_\*_AGGREGATABLE** makra mają wpływ na korzystanie z `CComObject`, `CComAggObject`, i `CComPolyObject`.  
  
 [Obsługa interfejsów IDispatch i IErrorInfo](../atl/supporting-idispatch-and-ierrorinfo.md)  
 Zawiera klasy implementacji ATL do użycia na potrzeby obsługi `IDispatch` i **IErrorInfo** interfejsów.  
  
 [Obsługa interfejsu IDispEventImpl](../atl/supporting-idispeventimpl.md)  
 W tym artykule omówiono kroki implementacji punktu połączenia dla klasy.  
  
 [Zmienianie domyślnej fabryki klas i modelu agregacji](../atl/changing-the-default-class-factory-and-aggregation-model.md)  
 Pokaż makra, jakie można użyć, aby zmienić klasy domyślny model fabryki i agregacji.  
  
 [Tworzenie obiektu zagregowanego](../atl/creating-an-aggregated-object.md)  
 Zawiera listę kroków tworzenia zagregowane obiektu.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Tworzenie projektu ATL](../atl/reference/creating-an-atl-project.md)  
 Zawiera informacje dotyczące tworzenia obiektu ATL COM.  
  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 Zawiera łącza do tematów koncepcyjne na temat programowania przy użyciu biblioteki Active Template Library.  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia](../atl/active-template-library-atl-concepts.md)

