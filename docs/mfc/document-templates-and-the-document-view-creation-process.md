---
title: Szablony dokumentów i proces tworzenia dokumentu-widoku
ms.date: 11/19/2018
helpviewer_keywords:
- icons, for multiple document templates
- document templates [MFC], and views
- document/view architecture [MFC], creating document/view
- single document template
- MFC, document templates
- multiple document template
- CDocTemplate class [MFC]
- templates [MFC], document templates
ms.assetid: 311ce4cd-fbdf-4ea1-a51b-5bb043abbcee
ms.openlocfilehash: b96a11926927e89890ca268dcff7d347079b25fb
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615776"
---
# <a name="document-templates-and-the-documentview-creation-process"></a>Szablony dokumentów i proces tworzenia dokumentu/widoku

Aby zarządzać złożonym procesem tworzenia dokumentów ze skojarzonymi z nimi widokami i oknami ramek, struktura używa dwóch klas szablonów dokumentu: [CSingleDocTemplate](reference/csingledoctemplate-class.md) dla aplikacji SDI i [CMULTIDOCTEMPLATE](reference/cmultidoctemplate-class.md) dla aplikacji MDI. `CSingleDocTemplate`Można utworzyć i zapisać jeden dokument jednego typu jednocześnie. `CMultiDocTemplate`Zachowuje listę wielu otwartych dokumentów jednego typu.

Niektóre aplikacje obsługują wiele typów dokumentów. Na przykład aplikacja może obsługiwać dokumenty tekstowe i dokumenty graficzne. W takiej aplikacji, gdy użytkownik wybierze polecenie nowe w menu plik, w oknie dialogowym zostanie wyświetlona lista możliwych nowych typów dokumentów do otwarcia. Dla każdego obsługiwanego typu dokumentu aplikacja używa odrębnego obiektu szablonu dokumentu. Na poniższej ilustracji przedstawiono konfigurację aplikacji MDI, która obsługuje dwa typy dokumentów i zawiera kilka otwartych dokumentów.

![Aplikacja MDI, która ma dwa typy dokumentów](../mfc/media/vc387h1.gif "Aplikacja MDI, która ma dwa typy dokumentów") <br/>
Aplikacja MDI z dwoma typami dokumentów

Szablony dokumentów są tworzone i obsługiwane przez obiekt aplikacji. Jednym z kluczowych zadań wykonywanych w ramach funkcji aplikacji `InitInstance` jest konstruowanie jednego lub większej liczby szablonów dokumentów odpowiedniego rodzaju. Ta funkcja jest opisana w temacie [Tworzenie szablonu dokumentu](document-template-creation.md). Obiekt aplikacji przechowuje wskaźnik do każdego szablonu dokumentu na liście szablonów i udostępnia interfejs do dodawania szablonów dokumentów.

Jeśli musisz obsługiwać dwa lub więcej typów dokumentów, musisz dodać dodatkowe wywołanie do [AddDocTemplate](reference/cwinapp-class.md#adddoctemplate) dla każdego typu dokumentu.

Ikona jest zarejestrowana dla każdego szablonu dokumentu na podstawie jego pozycji na liście szablonów dokumentów aplikacji. Kolejność szablonów dokumentów zależy od kolejności, w jakiej są dodawane, do `AddDocTemplate` . MFC założono, że pierwszy zasób ikony w aplikacji jest ikoną aplikacji, następnym zasobem ikony jest pierwsza ikona dokumentu itd.

Na przykład szablon dokumentu jest trzecią z trzech dla aplikacji. Jeśli w aplikacji znajduje się zasób ikony pod indeksem 3, ta ikona jest używana dla szablonu dokumentu. Jeśli nie, ikona pod indeksem 0 jest używana jako domyślna.

## <a name="see-also"></a>Zobacz też

[Tematy ogólne dotyczące MFC](general-mfc-topics.md)<br/>
[Tworzenie szablonu dokumentu](document-template-creation.md)<br/>
[Tworzenie dokumentu/widoku](document-view-creation.md)<br/>
[Relacje między obiektami MFC](relationships-among-mfc-objects.md)<br/>
[Tworzenie nowych dokumentów, okien i widoków](creating-new-documents-windows-and-views.md)
