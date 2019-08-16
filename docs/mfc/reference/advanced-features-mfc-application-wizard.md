---
title: Funkcje zaawansowane, kreator aplikacji MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.advanced
helpviewer_keywords:
- MFC Application Wizard, advanced features
ms.assetid: 8a6681c5-6576-4b12-841a-6862beee76fa
ms.openlocfilehash: dc2b745bf97dff65a3612c29745c9d0e455a347d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507811"
---
# <a name="advanced-features-mfc-application-wizard"></a>Funkcje zaawansowane, kreator aplikacji MFC

Ten temat zawiera listę opcji dodatkowych funkcji aplikacji, takich jak pomoc, obsługa drukowania i tak dalej. W każdej sekcji określ dodatkową pomoc techniczną dla tych zaawansowanych funkcji.

- **Pomoc kontekstowa (HTML)**

   Generuje zestaw plików pomocy dla pomocy kontekstowej, dostępne przy użyciu F1 i menu Pomoc lub klikając przycisk **Pomoc** w oknie dialogowym. Obsługa pomocy wymaga kompilatora plików pomocy. Jeśli nie masz kompilatora plików pomocy, o zainstaluj go, uruchamiając ponownie Instalatora.

   Zobacz [Pomoc HTML: Pomoc kontekstowa dla programów](../../mfc/html-help-context-sensitive-help-for-your-programs.md) i [plików pomocy (Pomoc HTML)](../../build/reference/help-files-html-help.md) , aby uzyskać więcej informacji.

- **Drukowanie i Podgląd wydruku**

   Generuje kod obsługujący polecenia drukowania, drukowania wydruku i podglądu wydruku poprzez wywoływanie funkcji Członkowskich w [klasie CView](../../mfc/reference/cview-class.md) z biblioteki MFC. Kreator dodaje także polecenia dla tych funkcji do menu aplikacji. Obsługa drukowania jest dostępna tylko dla aplikacji, które określają **obsługę architektury dokumentu/widoku** na stronie [Kreatora aplikacji MFC](../../mfc/reference/application-type-mfc-application-wizard.md) w kreatorze. Domyślnie aplikacje dokumentu/widoku mają obsługę drukowania.

- **Automatyzacja**

   Określa, że aplikacja może obsłużyć obiekty, które są implementowane w innej aplikacji, lub udostępnia aplikację klientom automatyzacji.

- **Kontrolki ActiveX**

   Obsługuje formanty ActiveX (ustawienie domyślne). Jeśli nie zaznaczysz tej opcji i chcesz później wstawić kontrolki ActiveX do projektu, musisz dodać wywołanie do [AfxEnableControlContainer —](ole-initialization.md#afxenablecontrolcontainer) w funkcji składowej [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) .

- **MAPI (interfejs API obsługi komunikatów)**

   Określa, że aplikacja może tworzyć, przesyłać i przechowywać wiadomości pocztowe oraz nimi manipulować.

- **Windows Sockets**

   Obsługuje usługi Windows sockets, które można wykorzystać do pisania aplikacji komunikujących się za pośrednictwem sieci TCP/IP.

- **Aktywne ułatwienia dostępu**

   Dodaje obsługę [IAccessible](/windows/win32/api/oleacc/nn-oleacc-iaccessible) do klas pochodnych [CWnd](../../mfc/reference/cwnd-class.md), za pomocą których można dostosować interfejs użytkownika w celu lepszego oddziaływania z klientami ułatwień dostępu.

- **Manifest formantów wspólnych**

   Domyślnie włączony. Generuje manifest aplikacji, aby włączyć bibliotekę DLL wspólnych formantów, która jest dołączona do systemu Microsoft Windows XP i nowszych systemów operacyjnych.

   Biblioteka DLL wspólnych formantów w wersji 6 nie uaktualnia automatycznie wcześniejszej wersji wspólnych formantów, z których korzystają istniejące aplikacje. Aby używać wersji 6 biblioteki DLL wspólnych formantów, należy utworzyć manifest aplikacji, instruujący aplikację, aby załadowała bibliotekę DLL. Ta biblioteka DLL wspólnych formantów obsługuje również kompozycje systemu Windows XP.

   Manifest aplikacji może również określić inne biblioteki DLL i wersje, których wymaga aplikacja. Aby uzyskać więcej informacji na temat manifestów aplikacji, zobacz [aplikacje izolowane i zestawy równoległe](/windows/win32/SbsCs/isolated-applications-and-side-by-side-assemblies-portal) w Windows SDK.

- **Obsługa Menedżera ponownego uruchamiania**

   Dodaje obsługę [Menedżera ponownego uruchamiania systemu Windows](/windows/win32/RstMgr/using-restart-manager). W tym filmie wideo pokazano, jak używać Menedżera ponownego uruchamiania z MFC: [Jak: Użyj nowego menedżera](/previous-versions/visualstudio/visual-studio-2010/dd831853(v%3dvs.100))ponownego uruchamiania.

- **Zaawansowane okienka ramki**

   |Opcja|Opis|
   |------------|-----------------|
   |**Okienko dokowania Eksploratora**|Tworzy okienko dokowania podobne do programu Visual Studio **Eksplorator rozwiązań** po lewej stronie okna głównego ramki.|
   |**Ramka dokowania wyjściowa**|Tworzy okienko dokowania podobne do okienka **danych wyjściowych** programu Visual Studio, które znajduje się w oknie głównej ramki.|
   |**Okienko dokowania właściwości**|Tworzy okienko dokowania podobne do okienka **Właściwości** programu Visual Studio po prawej stronie okna głównego ramki.|
   |**Okienko nawigacji**|Tworzy okienko dokowania, podobne do paska nawigacji programu Outlook, z lewej strony ramki głównego okna.|
   |**Pasek podpisu**|Tworzy pasek tytułu w stylu Office nad ramką głównego okna.|

- **Liczba plików na liście ostatnio używanych plików**

   Określa liczbę plików wymienionych na liście niedawno używanych. Liczbą domyślną jest 4.

## <a name="see-also"></a>Zobacz także

[Kreator aplikacji MFC](../../mfc/reference/mfc-application-wizard.md)
