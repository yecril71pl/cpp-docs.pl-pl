---
title: Zaawansowane funkcje, Kreator aplikacji MFC | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.appwiz.mfc.exe.advanced
dev_langs: C++
helpviewer_keywords: MFC Application Wizard, advanced features
ms.assetid: 8a6681c5-6576-4b12-841a-6862beee76fa
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5c2a9bb9ebb1837dc303e89e04ced496b52d1cdb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="advanced-features-mfc-application-wizard"></a>Funkcje zaawansowane, kreator aplikacji MFC
Ten temat zawiera listę opcji dodatkowych funkcji aplikacji, takich jak pomoc, obsługa drukowania i tak dalej. W każdej sekcji określ dodatkową pomoc techniczną dla tych zaawansowanych funkcji.  
  
 **Pomoc kontekstowa (HTML)**  
 Generuje zestaw plików pomocy dla pomocy kontekstowej dostępne przy użyciu F1 i menu Pomoc lub przez kliknięcie przycisku **pomocy** przycisk w oknie dialogowym. Obsługa pomocy wymaga kompilatora plików pomocy. Jeśli nie masz kompilatora plików pomocy, o zainstaluj go, uruchamiając ponownie Instalatora.  
  
 Zobacz [Pomoc HTML: Context-Sensitive Pomoc dla programów Your](../../mfc/html-help-context-sensitive-help-for-your-programs.md) i [pliki pomocy (Pomoc HTML)](../../ide/help-files-html-help.md) Aby uzyskać więcej informacji.  
  
 **Drukowania i podglądu wydruku**  
 Generuje kod w celu obsługi drukowania, drukować Instalatora i polecenia podglądu wydruku przez wywoływanie funkcji Członkowskich [cview — klasa](../../mfc/reference/cview-class.md) z biblioteki MFC. Kreator dodaje także polecenia dla tych funkcji do menu aplikacji. Obsługa drukowania jest dostępna tylko dla aplikacji, które określają **wsparcie dla architektury dokument/widok** w [typ aplikacji, Kreator aplikacji MFC](../../mfc/reference/application-type-mfc-application-wizard.md) stronie kreatora. Domyślnie aplikacje dokumentu/widoku mają obsługę drukowania.  
  
 **Automatyzacja**  
 Określa, że aplikacja może obsłużyć obiekty, które są implementowane w innej aplikacji, lub udostępnia aplikację klientom automatyzacji.  
  
 **Kontrolki ActiveX**  
 Obsługuje formanty ActiveX (ustawienie domyślne). Jeśli nie wybierz tę opcję, a później chcesz wstawić formantów ActiveX do projektu, należy dodać wywołanie [AfxEnableControlContainer](ole-initialization.md#afxenablecontrolcontainer) w aplikacji [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) elementu członkowskiego Funkcja.  
  
 **MAPI (interfejs API obsługi komunikatów)**  
 Określa, że aplikacja może tworzyć, przesyłać i przechowywać wiadomości pocztowe oraz nimi manipulować.  
  
 **Windows sockets**  
 Obsługuje usługi Windows sockets, które można wykorzystać do pisania aplikacji komunikujących się za pośrednictwem sieci TCP/IP.  
  
 **Active Accessibility**  
 Dodaje obsługę [IAccessible](http://msdn.microsoft.com/library/windows/desktop/dd318466) do [CWnd](../../mfc/reference/cwnd-class.md)-pochodzi z klasy, które można użyć do dostosowania interfejsu użytkownika dla lepszej interakcji z klientami ułatwień dostępu.  
  
 **Typowe kontrolki manifestu**  
 Domyślnie włączony. Generuje manifest aplikacji, aby włączyć bibliotekę DLL wspólnych formantów, która jest dołączona do systemu Microsoft Windows XP i nowszych systemów operacyjnych.  
  
 Biblioteka DLL wspólnych formantów w wersji 6 nie uaktualnia automatycznie wcześniejszej wersji wspólnych formantów, z których korzystają istniejące aplikacje. Aby używać wersji 6 biblioteki DLL wspólnych formantów, należy utworzyć manifest aplikacji, instruujący aplikację, aby załadowała bibliotekę DLL. Ta biblioteka DLL wspólnych formantów obsługuje również kompozycje systemu Windows XP.  
  
 Manifest aplikacji może również określić inne biblioteki DLL i wersje, których wymaga aplikacja. Aby uzyskać więcej informacji na temat manifestów aplikacji, zobacz [izolowanych aplikacji i zestawy Side-by-Side](http://msdn.microsoft.com/library/dd408052) w zestawie Windows SDK.  
  
 **Menedżer ponownego uruchamiania pomocy technicznej**  
 Dodaje obsługę [Menedżera ponownego uruchomienia systemu Windows](http://msdn.microsoft.com/library/windows/desktop/aa373680\(v=vs.85\).aspx). To wideo pokazuje, jak za pomocą Menedżera ponownego uruchomienia z MFC: [jak I: używają nowego Menedżera ponownego uruchomienia](http://msdn.microsoft.com/vstudio/ee886407).  
  
 **Okienka ramki zaawansowane**  
 |Opcja|Opis|  
|------------|-----------------|  
|**Okienko dokujące w Eksploratorze**|Okienko dokujące podobny programu Visual Studio tworzy **Eksploratora rozwiązań** na lewo od głównego okna ramowego.|  
|**Dane wyjściowe dokowania ramki**|Okienko dokujące podobny programu Visual Studio tworzy **dane wyjściowe** okienko, w którym znajduje się w obszarze głównego okna ramowego.|  
|**Właściwości dokujące okienko**|Okienko dokujące podobny programu Visual Studio tworzy **właściwości** w okienku po prawej stronie głównego okna ramowego.|  
|**Okienko nawigacji**|Tworzy okienko dokowania, podobne do paska nawigacji programu Outlook, z lewej strony ramki głównego okna.|  
|**Pasek tytułu**|Tworzy pasek tytułu w stylu Office nad ramką głównego okna.|  
  
 **Liczba plików na ostatnie pliki, lista**  
 Określa liczbę plików wymienionych na liście niedawno używanych. Liczbą domyślną jest 4.  
  
## <a name="see-also"></a>Zobacz też  
 [Kreator aplikacji MFC](../../mfc/reference/mfc-application-wizard.md)

