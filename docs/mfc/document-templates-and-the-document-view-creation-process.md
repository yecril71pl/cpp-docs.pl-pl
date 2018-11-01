---
title: Szablony dokumentów i proces tworzenia dokumentu widoku
ms.date: 11/04/2016
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
ms.openlocfilehash: 544a9bf60ee2066688703faa7e430e2337454e66
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50606352"
---
# <a name="document-templates-and-the-documentview-creation-process"></a>Szablony dokumentów i proces tworzenia dokumentu/widoku

Aby zarządzać złożony proces tworzenia dokumentów wraz z ich skojarzonych widoków i okien ramowych, środowisko wykorzystuje dwie klasy szablonów dokumentów: [CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md) dla aplikacji interfejsu SDI i [CMultiDocTemplate ](../mfc/reference/cmultidoctemplate-class.md) dla aplikacji MDI. Element `CSingleDocTemplate` można utworzyć i zapisać jeden dokument jeden typ w danym momencie. A `CMultiDocTemplate` przechowuje listę wiele otwartych dokumentów jednego typu.

Niektóre aplikacje obsługują wiele typów dokumentów. Na przykład aplikacja może obsługiwać dokumenty tekstowe i grafiki dokumentów. W aplikacji gdy użytkownik wybierze polecenie Nowy w menu Plik, okno dialogowe pokazuje listę możliwych typów dokumentu nowy, aby otworzyć. Dla każdego typu obsługiwanego dokumentu aplikacja używa obiektu szablonu dokumentu distinct. Na poniższym rysunku przedstawiono konfigurację aplikacji MDI, która obsługuje dwa typy dokumentów i pokazuje kilka otwartych dokumentów.

![Aplikacja MDI, która ma dwa typy dokumentów](../mfc/media/vc387h1.gif "vc387h1") aplikacji MDI za pomocą dwóch typów dokumentów

Szablony dokumentów są tworzone i konserwowane przez obiekt aplikacji. Jedną z kluczowych zadań wykonywanych podczas aplikacji `InitInstance` funkcja jest do konstruowania co najmniej jeden szablon dokumentu, tego rodzaju odpowiedniej. Ta funkcja jest opisana w [Tworzenie szablonu dokumentu](../mfc/document-template-creation.md). Obiekt aplikacja przechowuje wskaźnik do każdego szablonu dokumentu na liście szablonów i udostępnia interfejs umożliwiający dodanie szablonów dokumentów.

Jeśli potrzebujesz do obsługi co najmniej dwóch typów dokumentów, należy dodać dodatkowy wywołanie [AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate) dla każdego typu dokumentu.

Ikona jest zarejestrowany dla każdego szablonu dokumentu, na podstawie jego pozycji na liście aplikacji szablonów dokumentów. Kolejność szablonów dokumentów jest określana przez kolejność są dodawane przy użyciu wywołań `AddDocTemplate`. MFC przyjęto założenie, że pierwszy zasobu ikony w aplikacji znajduje się ikona aplikacji, następnym zasobu ikony pierwsza ikona dokumentu i tak dalej.

Na przykład szablon dokumentu jest trzeci trzech dla aplikacji. W przypadku zasobu ikony aplikacji o indeksie 3, ta ikona służy do szablonu dokumentu. W przeciwnym razie ikona pod indeksem 0 jest używany jako domyślny.

## <a name="see-also"></a>Zobacz też

[Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)<br/>
[Tworzenie szablonu dokumentu](../mfc/document-template-creation.md)<br/>
[Tworzenie dokumentu/widoku](../mfc/document-view-creation.md)<br/>
[Relacje między obiektami MFC](../mfc/relationships-among-mfc-objects.md)<br/>
[Tworzenie nowych dokumentów, okien i widoków](../mfc/creating-new-documents-windows-and-views.md)

