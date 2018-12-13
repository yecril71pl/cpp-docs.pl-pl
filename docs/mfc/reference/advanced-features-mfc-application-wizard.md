---
title: Funkcje zaawansowane, kreator aplikacji MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.advanced
helpviewer_keywords:
- MFC Application Wizard, advanced features
ms.assetid: 8a6681c5-6576-4b12-841a-6862beee76fa
ms.openlocfilehash: 1af16f7009ceb97ea86d641f47cf56ea5a398c26
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694299"
---
# <a name="advanced-features-mfc-application-wizard"></a>Funkcje zaawansowane, kreator aplikacji MFC

Ten temat zawiera listę opcji dodatkowych funkcji aplikacji, takich jak pomoc, obsługa drukowania i tak dalej. W każdej sekcji określ dodatkową pomoc techniczną dla tych zaawansowanych funkcji.

- **Pomoc kontekstowa (HTML)**

   Generuje zestaw plików pomocy dla pomocy kontekstowej, dostępnej za pomocą menu Pomoc i F1 lub klikając **pomocy** przycisku w oknie dialogowym. Obsługa pomocy wymaga kompilatora plików pomocy. Jeśli nie masz kompilatora plików pomocy, o zainstaluj go, uruchamiając ponownie Instalatora.

   Zobacz [Pomoc HTML: pomoc kontekstowa do programów](../../mfc/html-help-context-sensitive-help-for-your-programs.md) i [pliki pomocy (Pomoc HTML)](../../ide/help-files-html-help.md) Aby uzyskać więcej informacji.

- **Drukowanie i Podgląd wydruku**

   Generuje kod w celu obsługi drukowania, konfiguracji drukowania i podglądu wydruku poleceń przez wywołanie funkcji składowych [CView Class](../../mfc/reference/cview-class.md) z biblioteki MFC. Kreator dodaje także polecenia dla tych funkcji do menu aplikacji. Obsługa drukowania jest dostępna tylko w przypadku aplikacji, które określają **Obsługa architektury dokument/widok** w [typ aplikacji, Kreator aplikacji MFC](../../mfc/reference/application-type-mfc-application-wizard.md) strony kreatora. Domyślnie aplikacje dokumentu/widoku mają obsługę drukowania.

- **Automatyzacja**

   Określa, że aplikacja może obsłużyć obiekty, które są implementowane w innej aplikacji, lub udostępnia aplikację klientom automatyzacji.

- **Kontrolki ActiveX**

   Obsługuje formanty ActiveX (ustawienie domyślne). Jeśli nie wybierz tę opcję, a później chcesz wstawić formanty ActiveX do projektu, należy dodać wywołanie [afxenablecontrolcontainer —](ole-initialization.md#afxenablecontrolcontainer) w Twojej aplikacji [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) elementu członkowskiego Funkcja.

- **MAPI (Messaging API)**

   Określa, że aplikacja może tworzyć, przesyłać i przechowywać wiadomości pocztowe oraz nimi manipulować.

- **Windows sockets**

   Obsługuje usługi Windows sockets, które można wykorzystać do pisania aplikacji komunikujących się za pośrednictwem sieci TCP/IP.

- **Active Accessibility**

   Dodaje obsługę [IAccessible](/windows/desktop/api/oleacc/nn-oleacc-iaccessible) do [CWnd](../../mfc/reference/cwnd-class.md)-pochodne klasy, które umożliwia dostosowywanie interfejsu użytkownika w celu lepszej interakcji z klientami ułatwień dostępu.

- **Typowe formant manifestu**

   Domyślnie włączony. Generuje manifest aplikacji, aby włączyć bibliotekę DLL wspólnych formantów, która jest dołączona do systemu Microsoft Windows XP i nowszych systemów operacyjnych.

   Biblioteka DLL wspólnych formantów w wersji 6 nie uaktualnia automatycznie wcześniejszej wersji wspólnych formantów, z których korzystają istniejące aplikacje. Aby używać wersji 6 biblioteki DLL wspólnych formantów, należy utworzyć manifest aplikacji, instruujący aplikację, aby załadowała bibliotekę DLL. Ta biblioteka DLL wspólnych formantów obsługuje również kompozycje systemu Windows XP.

   Manifest aplikacji może również określić inne biblioteki DLL i wersje, których wymaga aplikacja. Aby uzyskać więcej informacji na temat manifestów aplikacji, zobacz [izolowanymi oraz aplikacjami wykonywanymi Side-by-Side](/windows/desktop/SbsCs/isolated-applications-and-side-by-side-assemblies-portal) w zestawie Windows SDK.

- **Obsługa Menedżera ponownego uruchamiania**

   Dodaje obsługę [Menedżera ponownego uruchamiania Windows](/windows/desktop/RstMgr/using-restart-manager). Ten film pokazuje, jak używać Menedżera ponownego uruchamiania MFC: [jak używać nowego Menedżera ponownego uruchamiania](/previous-versions/visualstudio/visual-studio-2010/dd831853(v%3dvs.100)).

- **Zaawansowane okienka ramki**

   |Opcja|Opis|
   |------------|-----------------|
   |**Okienko dokowania Eksploratora**|Tworzy okienko dokowania, podobne programu Visual Studio **Eksploratora rozwiązań** z lewej strony ramki głównego okna.|
   |**Ramka dokowania danych wyjściowych**|Tworzy okienko dokowania, podobne programu Visual Studio **dane wyjściowe** okienko, w którym znajduje się w oknie głównym ramki.|
   |**Okienko dokowania właściwości**|Tworzy okienko dokowania, podobne programu Visual Studio **właściwości** w okienku z prawej strony ramki głównego okna.|
   |**Okienko nawigacji**|Tworzy okienko dokowania, podobne do paska nawigacji programu Outlook, z lewej strony ramki głównego okna.|
   |**Pasek podpisu**|Tworzy pasek tytułu w stylu Office nad ramką głównego okna.|

- **Liczba plików na liście niedawno używanych plików**

   Określa liczbę plików wymienionych na liście niedawno używanych. Liczbą domyślną jest 4.

## <a name="see-also"></a>Zobacz też

[Kreator aplikacji MFC](../../mfc/reference/mfc-application-wizard.md)

