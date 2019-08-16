---
title: Wprowadzenie do ATL
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- COM objects, creating in ATL
- ATL
ms.assetid: 77f565e8-c4ec-4a80-af4b-7278fcfe5c98
ms.openlocfilehash: 5eba816bc87eeebea2c41489a5d15c48645739e8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492110"
---
# <a name="introduction-to-atl"></a>Wprowadzenie do ATL

ATL to Active Template Library, zestaw klas opartych na C++ szablonach, za pomocą których można łatwo tworzyć małe, szybkie Component Object Model obiekty (com). Ma ona specjalne wsparcie dla kluczowych funkcji com, takich jak: implementacje giełdowe [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown), [elementu IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory), `IDispatch` [IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2)i; podwójne interfejsy; standardowe interfejsy modułu wyliczającego com; punkty połączeń; wycofywanie interfejsów i kontrolki ActiveX.

Kod ATL może służyć do tworzenia obiektów jednowątkowych, obiektów typu Apartment, obiektów modelu dowolnego wątkowego lub obiektów typu "Free-threaded" i modelu Apartment.

Tematy omówione w tej sekcji obejmują:

- Jak [Biblioteka szablonów](../atl/using-a-template-library.md) różni się od biblioteki standardowej.

- Co możesz [zrobić i nie można wykonać z ATL](../atl/scope-of-atl.md).

- [Zalecenia dotyczące wybierania między ATL i MFC](../atl/recommendations-for-choosing-between-atl-and-mfc.md).

## <a name="see-also"></a>Zobacz także

[Wprowadzenie do modelu COM i ATL](../atl/introduction-to-com-and-atl.md)
