---
title: Wprowadzenie do ATL | Dokumentacja firmy Microsoft
ms.custom: index-page
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- COM objects, creating in ATL
- ATL
ms.assetid: 77f565e8-c4ec-4a80-af4b-7278fcfe5c98
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 93baa57e8567b6ab08a0157f200a4d89fc9813e4
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43754845"
---
# <a name="introduction-to-atl"></a>Wprowadzenie do ATL

ATL jest biblioteki Active Template Library, zestaw oparty na szablonie C++ klasy przy użyciu której możesz łatwo tworzyć małe, szybkie obiektów Component Object Model (COM). Ma specjalne pomocy technicznej w przypadku kluczowych funkcji COM, w tym: podstawowy implementacje [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown), [IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory), [IClassFactory2](/windows/desktop/api/ocidl/nn-ocidl-iclassfactory2), i `IDispatch`; podwójne interfejsów; standardowe interfejsy modułu wyliczającego COM; punkty połączenia; interfejsy odrywania; i formantów ActiveX.

Kod ATL może być używany do tworzenia jednowątkowych obiektów, obiekty modelu typu apartment, bezwątkowy modelu obiektów lub obiekty bezwątkowy i modelu typu apartment.

Tematy omówione w tej sekcji obejmują:

- Jak [Biblioteka szablonów](../atl/using-a-template-library.md) różni się od biblioteki standardowej.

- Tym, co [można i nie będzie możliwe ATL](../atl/scope-of-atl.md).

- [Zalecenia dotyczące wybierania między ATL i MFC](../atl/recommendations-for-choosing-between-atl-and-mfc.md).

## <a name="see-also"></a>Zobacz też

[Wprowadzenie do modelu COM i ATL](../atl/introduction-to-com-and-atl.md)

