---
title: MFC COM
ms.date: 09/12/2018
f1_keywords:
- MFC COM (MFC)
helpviewer_keywords:
- MFC, COM support
- MFC ActiveX controls [MFC], COM support in MFC
- MFC COM [MFC]
- ActiveX controls [MFC], COM object model
- Active technology [MFC]
- COM [MFC], MFC support
ms.assetid: 7646bdcb-3a06-4ed5-9386-9b00f3979dcb
ms.openlocfilehash: 514251475050e728be1959417ead1dbdf96e4800
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358194"
---
# <a name="mfc-com"></a>MFC COM

Podzbiór MFC jest przeznaczony do obsługi com, podczas gdy większość biblioteki aktywnych szablonów (ATL) jest przeznaczony do programowania COM. W tej sekcji tematów opisano obsługę MFC dla modelu COM.

Aktywne technologie (takie jak formanty ActiveX, Aktywna hermetyzacja dokumentu, OLE itd.) używają modelu COM (Component Object Model), aby umożliwić składnikom oprogramowania interakcję ze sobą w środowisku sieciowym, niezależnie od języka, w którym zostały utworzone. Aktywne technologie mogą być używane do tworzenia aplikacji działających na pulpicie lub w Internecie. Aby uzyskać więcej informacji, zobacz [Wprowadzenie do modelu COM](../atl/introduction-to-com.md) lub Modelu obiektu [komponentu](/windows/win32/com/the-component-object-model).

Aktywne technologie obejmują zarówno technologie klienta, jak i serwerów, w tym:

- Formanty ActiveX są interaktywnymi obiektami, które mogą być używane w kontenerach, takich jak witryna sieci Web. Aby uzyskać więcej informacji na temat formantów ActiveX, zobacz:

  - [Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)

  - [Kontrolki ActiveX w Internecie](../mfc/activex-controls-on-the-internet.md)

  - [Przegląd: Internet](../mfc/mfc-internet-programming-basics.md)

  - [Uaktualnianie istniejącego formantu ActiveX do użycia w Internecie](../mfc/upgrading-an-existing-activex-control.md)

  - [Debugowanie formantu ActiveX](/visualstudio/debugger/how-to-debug-an-activex-control)

- Aktywne skrypty sterują zintegrowanym zachowaniem jednego lub większej liczby formantów ActiveX z przeglądarki lub serwera. Aby uzyskać więcej informacji na temat aktywnego skryptów, zobacz [Active Technology w Internecie](../mfc/active-technology-on-the-internet.md).

- [Automatyzacja](../mfc/automation.md) (wcześniej znany jako automatyzacji OLE) umożliwia jednej aplikacji do manipulowania obiektami zaimplementowanymi w innej aplikacji lub "uwidaczniać" obiekty, dzięki czemu mogą być manipulowane.

   Obiekt zautomatyzowany może być lokalny lub zdalny (na innym komputerze dostępnym w sieci). Automatyzacja jest dostępna dla obiektów OLE i COM.

- Ta sekcja zawiera również informacje na temat sposobu pisania składników COM przy użyciu MFC, na przykład w [punktach połączenia](../mfc/connection-points.md).

Aby zapoznać się z omówienia tego, co nadal nazywa się OLE w porównaniu z tym, co jest obecnie nazywane aktywną technologią, zobacz tematy [ole](../mfc/ole-in-mfc.md).

## <a name="in-this-section"></a>W tej sekcji

[Zawieranie dokumentów aktywnych](../mfc/active-document-containment.md)

[Automatyzacja](../mfc/automation.md)

[Punkty połączenia](../mfc/connection-points.md)

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)

## <a name="see-also"></a>Zobacz też

[Pojęcia](../mfc/mfc-concepts.md)
