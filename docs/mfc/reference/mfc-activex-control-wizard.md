---
title: Kreator formantów MFC ActiveX
ms.date: 09/12/2018
f1_keywords:
- vc.appwiz.mfc.ctl.overview
helpviewer_keywords:
- ActiveX controls [MFC], MFC
- MFC ActiveX controls [MFC], wizards
- OLE controls [MFC], creating
- MFC ActiveX Control Wizard
- OLE controls [MFC]
ms.assetid: f19d698c-bdc3-4c74-af97-3d6ccb441b75
ms.openlocfilehash: cec4c3aa6aedfa7a1f8234c6cc2355970d453f56
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822681"
---
# <a name="mfc-activex-control-wizard"></a>Kreator formantów MFC ActiveX

Kontrolki ActiveX jest określonego typu [serwer automatyzacji](../../mfc/automation-servers.md); jest komponentów wielokrotnego użytku. Hosting kontrolek ActiveX aplikacji jest [klienta automatyzacji](../../mfc/automation-clients.md) tej kontrolki. Jeśli do tworzenia składników wielokrotnego użytku, użyj tego kreatora do tworzenia kontrolki. Zobacz [kontrolki ActiveX MFC](../../mfc/mfc-activex-controls.md) Aby uzyskać więcej informacji.

>[!IMPORTANT]
> ActiveX jest technologią starszą, która nie powinny być używane w przypadku nowych wdrożeń. Aby uzyskać więcej informacji na temat nowych technologii, które zastępują ActiveX zobacz [formantów ActiveX](../activex-controls.md).

Alternatywnie można utworzyć automatyzacji serwera MFC aplikacji za pomocą [Kreator aplikacji MFC](../../mfc/reference/mfc-application-wizard.md).

Kontrolki ActiveX utworzona za pomocą tego kreatora można mieć interfejsu użytkownika lub może być niewidoczna. Można określić tę opcję w [ustawienia kontroli](../../mfc/reference/control-settings-mfc-activex-control-wizard.md) strony kreatora. Kontrolka czasomierza znajduje się przykład formantu ActiveX, który ma być niewidoczna.

Kontrolki ActiveX może mieć interfejs użytkownika złożone. Niektóre kontrolki mogą być takich jak formularze zhermetyzowany: jeden formant zawierające wiele pól każdy formant Windows samodzielną. Na przykład obiekt części automatycznie implementowana jako formant MFC ActiveX mogą stanowić interfejs użytkownika podobne do formularza za pomocą którego użytkownicy mogą odczytywać i edytować numer części, Nazwa części i inne informacje. Zobacz [kontrolki ActiveX MFC](../../mfc/mfc-activex-controls.md) Aby uzyskać więcej informacji.

Jeśli musisz utworzyć kontener dla obiektów ActiveX, zobacz [utworzyć kontener formantu ActiveX](../../mfc/reference/creating-an-mfc-activex-control-container.md).

MFC starter program zawiera pliki źródłowe (.cpp) języka C++, pliki zasobów (.rc) i plik projektu (.vcxproj). Kod wygenerowany w tych plikach startowych jest oparty na MFC.

Na poniższej liście przykład przedstawiono zadania i typy rozszerzeń dla formantu ActiveX:

- [Optymalizacja formantu ActiveX](../../mfc/mfc-activex-controls-optimization.md)

- [Dodawanie zdarzeń standardowych do kontrolki ActiveX](../../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md)

- [Dodawanie zdarzeń niestandardowych](../../mfc/mfc-activex-controls-adding-custom-events.md)

- [Dodawanie metod standardowych](../../mfc/mfc-activex-controls-adding-stock-methods.md)

- [Dodawanie metod niestandardowych](../../mfc/mfc-activex-controls-adding-custom-methods.md)

- [Dodawanie właściwości standardowych](../../mfc/mfc-activex-controls-adding-stock-properties.md)

- [Dodawanie właściwości niestandardowych](../../mfc/mfc-activex-controls-adding-custom-properties.md)

- [Programowanie kontrolek ActiveX w kontenerze kontrolek ActiveX](../../mfc/programming-activex-controls-in-a-activex-control-container.md)

## <a name="overview"></a>Omówienie

Ta strona kreatora opisuje bieżące ustawienia aplikacji dla projektu kontrolki MFC ActiveX, który tworzysz. Domyślnie kreator tworzy projekt w następujący sposób:

- Domyślny projekt generuje pliki licencji lub pomocy nie czasu wykonywania. Te ustawienia domyślne można zmienić na [ustawienia aplikacji](../../mfc/reference/application-settings-mfc-activex-control-wizard.md) strony. Tylko wybrane opcje na tej stronie kreatora kontrolek ActiveX są odzwierciedlane **Przegląd** strony.

- Projekt zawiera klasy kontrolki i właściwości klasy strony, na podstawie nazwy projektu. Można edytować nazwy, nazwa projektu i pliku na [nazw kontrolek](../../mfc/reference/control-names-mfc-activex-control-wizard.md) strony.

- Formant opiera się na nie istniejące kontrolki Windows, aktywuje staje się widoczny, ma interfejs użytkownika, i obejmuje **o** okno dialogowe. Te ustawienia domyślne można zmienić na [ustawienia kontroli](../../mfc/reference/control-settings-mfc-activex-control-wizard.md) strony.

## <a name="see-also"></a>Zobacz także

[Tworzenie i zarządzanie projektami Visual C++](../../build/creating-and-managing-visual-cpp-projects.md)<br/>
[Typy projektów Visual C++](../../build/reference/visual-cpp-project-types.md)<br/>
[Pojęcia](../../atl/active-template-library-atl-concepts.md)
