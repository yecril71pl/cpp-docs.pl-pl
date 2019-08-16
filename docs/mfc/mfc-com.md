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
ms.openlocfilehash: eab688022c311f3d20fc092736ee4c7d37232a43
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508094"
---
# <a name="mfc-com"></a>MFC COM

Podzbiór MFC jest przeznaczony do obsługi modelu COM, podczas gdy większość Active Template Library (ATL) jest zaprojektowana do programowania COM. W tej części tematów opisano obsługę modelu COM w programie MFC.

Technologie aktywne (takie jak kontrolki ActiveX, dokumenty aktywne zawiera, OLE i tak dalej) używają Component Object Model (COM), aby umożliwić składnikom oprogramowania współdziałanie ze sobą w środowisku sieciowym, niezależnie od języka, w którym zostały utworzony. Aktywne technologie mogą służyć do tworzenia aplikacji uruchamianych na pulpicie lub w Internecie. Aby uzyskać więcej informacji, zobacz [wprowadzenie do modelu COM](../atl/introduction-to-com.md) lub [Component Object Model](/windows/win32/com/the-component-object-model).

Technologie aktywne obejmują technologie klienta i serwera, w tym następujące:

- Formanty ActiveX są obiektami interaktywnymi, które mogą być używane w kontenerach, takich jak witryna sieci Web. Aby uzyskać więcej informacji na temat kontrolek ActiveX, zobacz:

   - [Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)

   - [Kontrolki ActiveX w Internecie](../mfc/activex-controls-on-the-internet.md)

   - [Podsumowanie Internet](../mfc/mfc-internet-programming-basics.md)

   - [Uaktualnianie istniejącej kontrolki ActiveX do użycia w Internecie](../mfc/upgrading-an-existing-activex-control.md)

   - [Debugowanie kontrolki ActiveX](/visualstudio/debugger/how-to-debug-an-activex-control)

- Aktywne skrypty kontroluje zintegrowane zachowanie co najmniej jednej kontrolki ActiveX z przeglądarki lub serwera. Aby uzyskać więcej informacji na temat aktywnych skryptów, zobacz [aktywną technologię w Internecie](../mfc/active-technology-on-the-internet.md).

- [Automatyzacja](../mfc/automation.md) (dawniej znana jako Automatyzacja OLE) umożliwia jednej aplikacji manipulowanie obiektami zaimplementowanymi w innej aplikacji lub obiektów "uwidaczniania", dzięki czemu można manipulować nimi.

   Obiekt zautomatyzowany może być lokalny lub zdalny (na innym komputerze dostępnym w sieci). Automatyzacja jest dostępna zarówno dla obiektów OLE, jak i COM.

- Ta sekcja zawiera również informacje dotyczące sposobu pisania składników COM za pomocą MFC, na przykład w [punktach połączenia](../mfc/connection-points.md).

Aby zapoznać się z informacjami o tym, co jest nadal nazywane technologią OLE, a teraz nazywamy technologię Active, zapoznaj się z tematami dotyczącymi [OLE](../mfc/ole-in-mfc.md).

## <a name="in-this-section"></a>W tej sekcji

[Zawieranie dokumentów aktywnych](../mfc/active-document-containment.md)

[Automatyzacja](../mfc/automation.md)

[Punkty połączenia](../mfc/connection-points.md)

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)

## <a name="see-also"></a>Zobacz także

[Pojęcia](../mfc/mfc-concepts.md)
