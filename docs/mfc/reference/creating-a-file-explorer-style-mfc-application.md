---
title: Tworzenie aplikacji MFC w stylu eksploratora plików
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfcexplorer.project
helpviewer_keywords:
- browsers [MFC], Explorer-style applications
- MFC applications [MFC], Windows Explorer-style
- Explorer-style applications [MFC], creating
ms.assetid: f843ab5d-2d5d-41ca-88a4-badc0d2f8052
ms.openlocfilehash: 16969b7ef9c0447dfce971af8d329c5b93367041
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62372247"
---
# <a name="creating-a-file-explorer-style-mfc-application"></a>Tworzenie aplikacji MFC w stylu eksploratora plików

Wiele aplikacji systemu Windows przy użyciu interfejsu użytkownika (UI) dla Eksploratora plików. Po uruchomieniu Eksploratora plików, na przykład, zobaczysz aplikacji za pomocą rozdzielacz pionowy pasek podziału obszaru klienta. Po lewej stronie obszaru klienckiego zapewnia nawigacji i funkcji przeglądania, a po prawej stronie obszaru klienta zawiera szczegóły dotyczące wyboru w okienku po lewej stronie. Gdy użytkownik kliknie element w okienku po lewej stronie, aplikacja repopulates w okienku po prawej stronie. W aplikacji MDI, można użyć poleceń na **widoku** menu, aby zmienić liczbę szczegółów wyświetlane w okienku po prawej stronie. (W SDI lub wiele dokumentów najwyższego poziomu aplikacji, można zmienić szczegóły, korzystając z przycisków paska narzędzi.)

Zawartość okienka zależą od aplikacji. W przeglądarce systemu plików okienka po lewej stronie wyświetla hierarchiczny widok katalogów lub komputery lub grupy maszyn, podczas gdy w okienku po prawej stronie wyświetla foldery, pojedyncze pliki, lub maszyn i szczegółowe informacje o nich. Zawartość nie muszą być jako plików. Może być wiadomości e-mail, raportów o błędach lub innych elementów w bazie danych.

Kreator tworzy następujące klasy:

- `CLeftView` Klasa definiuje okienka po lewej stronie obszaru klienta. Zawsze jest pochodną [CTreeView](../../mfc/reference/ctreeview-class.md).

- C*ProjName*widoku klasy definiuje w okienku po prawej stronie obszaru klienta. Domyślnie jest on tworzony na podstawie [CListView](../../mfc/reference/clistview-class.md) , ale może być inny rodzaj widoku, w zależności od klasy, wystarczy podać z **klasy bazowej** listy w [wygenerowane klasy](../../mfc/reference/generated-classes-mfc-application-wizard.md) strony Kreator.

Wygenerowanej aplikacji może mieć interfejsu pojedynczego dokumentu (SDI), mechanizm interfejsu wielu dokumentów (MDI) lub wielu architektura dokumentów najwyższego poziomu. Każde okno ramki, aplikacja tworzy w pionie dzieli się przy użyciu [CSplitterWnd](../../mfc/reference/csplitterwnd-class.md). Kodowanie ten typ aplikacji jest podobny do kodowania normalne aplikacji MFC, która używa podziału, z tą różnicą, że ten typ aplikacji ma widoków oddzielnej kontrolce w każde okienko rozdzielacza.

Jeśli używasz domyślny widok listy w okienku po prawej stronie, Kreator tworzy dodatkowym menu niezwykle szerokie możliwości (tylko aplikacje MDI) i przycisków paska narzędzi, aby przełączyć stylu widoku duże ikony, małe ikony, listy i szczegółów tryby.

### <a name="to-begin-creating-a-file-explorer-style-mfc-executable"></a>Aby rozpocząć tworzenie pliku wykonywalnego MFC w stylu Eksploratora plików

1. Postępuj zgodnie z instrukcjami [tworzenie aplikacji MFC](../../mfc/reference/creating-an-mfc-application.md).

1. W Kreatorze aplikacji MFC [typ aplikacji](../../mfc/reference/application-type-mfc-application-wizard.md) wybierz opcję **Eksploratora plików** projektu stylu.

1. Ustaw inne opcje, które chcesz na pozostałych stronach kreatora.

1. Kliknij przycisk **Zakończ** do zostanie wygenerowany szkielet aplikacji.

Aby uzyskać więcej informacji, zobacz:

- [Wiele typów dokumentów, widoków i okien ramowych](../../mfc/multiple-document-types-views-and-frame-windows.md)

- [Pochodne klasy widoków](../../mfc/derived-view-classes-available-in-mfc.md)

- [Opcje do wyboru przy projektowaniu aplikacji](../../mfc/application-design-choices.md)

## <a name="see-also"></a>Zobacz także

[Kreator aplikacji MFC](../../mfc/reference/mfc-application-wizard.md)<br/>
[Tworzenie aplikacji MFC w stylu przeglądarki internetowej](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)<br/>
[Tworzenie aplikacji MFC opartej na formularzach](../../mfc/reference/creating-a-forms-based-mfc-application.md)
