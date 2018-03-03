---
title: "Funkcje interfejsu użytkownika, Kreator aplikacji MFC | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.appwiz.mfc.exe.ui
dev_langs:
- C++
helpviewer_keywords:
- MFC Application Wizard, user interface features
ms.assetid: 59e7b829-a665-42eb-be23-3f2a36eb2dad
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5906cf607e09df536825eed88e7b1be59d8fdee2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="user-interface-features-mfc-application-wizard"></a>Funkcje interfejsu użytkownika, kreator aplikacji MFC
W tym temacie opisano opcje używane do określania wyglądu aplikacji. Funkcje interfejsu użytkownika dostępne dla projektu są zależne od typu aplikacji określonej w [typ aplikacji, Kreator aplikacji MFC](../../mfc/reference/application-type-mfc-application-wizard.md) Kreatora aplikacji MFC. Na przykład można utworzyć aplikację interfejsu pojedynczego dokumentu, nie można dodać style ramki podrzędnych.  
  
 **Style ramki głównej**  
 Ustawia funkcje ramki okna głównego aplikacji.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Grubą ramką**|Tworzy okno obramowaniem zmiany rozmiaru. Domyślnie.|  
|**Pole minimalizacji**|Zawiera pole minimalizacji głównego okna ramowego. Domyślnie.|  
|**Pole maksymalizacji**|Zawiera pole maksymalizacji głównego okna ramowego. Domyślnie.|  
|**Zminimalizowany**|Otwiera główną ramkę okna w postaci ikony.|  
|**Zmaksymalizowane**|Otwiera okno ramowe głównego do pełnego rozmiaru ekranu.|  
|**Menu systemowe**|Zawiera menu systemowe w głównego okna ramowego. Domyślnie.|  
|**Pole informacji**|Obejmuje **o** pole dla aplikacji. Użytkownik ma dostęp to pole z poziomu aplikacji **pomocy** menu. Wartość domyślna i zmieniać dopiero po wybraniu **okno dialogowe na podstawie**w [typ aplikacji, Kreator aplikacji MFC](../../mfc/reference/application-type-mfc-application-wizard.md) strony.<br /><br /> **Uwaga** zazwyczaj niedostępne opcję oznacza, że kreatora nie zastosowania opcji do projektu, czy element niedostępny pole wyboru jest zaznaczone lub wyczyszczone. W takim przypadku Kreator zawsze dodaje **o** pola do projektu, chyba że określony projekt jako okna dialogowego na podstawie i usuń zaznaczenie pola.|  
|**Pasek stanu początkowego**|Dodaje pasek stanu do aplikacji. Pasek stanu zawiera automatyczne wskaźników klawiatury włączony klawisz CAPS LOCK, NUM LOCK i blokady PRZEWIJANIA kluczy i wiersz wiadomości, który wyświetla Pomoc parametrów dla polecenia menu i paska narzędzi przycisków. Po kliknięciu tej opcji doda również polecenia menu, aby wyświetlić lub ukryć pasek stanu. Domyślnie aplikacja ma paska stanu. Nie jest dostępna dla typów aplikacji opartych na oknach dialogowych.|  
|**Okna podziału**|Udostępnia pasek podziału. Pasek podziału dzieli widoków aplikacji. W wielu aplikacji interfejsu (MDI) dokumentu ramki podrzędnych MDI klienta okno jest oknem podziału, a w aplikacji (SDI) interfejsu pojedynczego dokumentu i wielu aplikacji na najwyższym poziomie dokumentu główną ramkę okna klienta okna podziału. Nie jest dostępna dla typów aplikacji opartych na oknach dialogowych.|  
  
 **Style ramki podrzędne**  
 Określa wygląd i stan początkowy ramek podrzędnych w aplikacji. Style ramki podrzędne są dostępne tylko aplikacje MDI.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Pole minimalizacji podrzędne**|Określa, czy okno podrzędne ma przycisk Minimalizuj (domyślnie włączony).|  
|**Pole maksymalizacji podrzędne**|Określa, czy okno podrzędne znajduje się przycisk Maksymalizuj (domyślnie włączony).|  
|**Zmaksymalizowane podrzędne**|Określa, czy okno podrzędne jest początkowo zmaksymalizowane przez ustawienie flagi cs.style **ws_maximize —** w [PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow) funkcji członkowskiej klasy `CChildFrame`.|  
  
 **Paski poleceń (menu/pasek narzędzi/Wstążka)**  
 Wskazuje, czy aplikacja zawiera menu, paski narzędzi i/lub wstążki. Nie jest dostępna dla aplikacji opartych na oknach dialogowych.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Użyj klasycznego menu**|Określa, czy aplikacja zawiera menu klasycznego, możliwością przeciągania.|  
|**Użyj klasycznego, dokującego paska narzędzi**|Dodaje standardowych narzędzi systemu Windows do aplikacji. Pasek narzędzi zawiera przyciski do tworzenia nowego dokumentu; Otwieranie i zapisywanie plików dokumentu. Wycinanie, kopiowanie, wklejanie lub drukowanie tekstu. i trybu pomocy. Włączenie tej opcji doda również polecenia menu umożliwia wyświetlanie lub ukrywanie paska narzędzi.|  
|**Użyj paska narzędzi stylu przeglądarki**|Dodaje paska narzędzi w stylu Eksploratora Internetu do aplikacji.|  
|**Użyj paska menu i paska narzędzi**|Wskazuje, że aplikacja zawiera pasek możliwością przeciągania menu i paska narzędzi.|  
|**Zdefiniowane przez użytkownika paski narzędzi i obrazy**|Umożliwia to użytkownikowi dostosowywanie paska narzędzi i obrazy pasków narzędzi w czasie wykonywania.|  
|**Zachowanie spersonalizowane menu**|Określa, czy menu zawiera pełną listę elementów po otwarciu lub jeśli zawiera tylko polecenia najczęściej wykorzystywanych przez użytkowników.|  
|**Użyj wstążki**|Używa wstążki pakietu Office 2007 przypominającej aplikacji zamiast na pasku menu lub pasek narzędzi.|  
  
 **Tytuł okna dialogowego**  
 Aby uzyskać [cdialog — klasa](../../mfc/reference/cdialog-class.md)— aplikacje oparte na tylko ten tytuł pojawi się na pasku tytułu okna dialogowego. Aby edytować tego pola, musisz najpierw wybrać **okno dialogowe na podstawie** opcję w obszarze **typu aplikacji**. Aby uzyskać więcej informacji, zobacz [typ aplikacji, Kreator aplikacji MFC](../../mfc/reference/application-type-mfc-application-wizard.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Kreator aplikacji MFC](../../mfc/reference/mfc-application-wizard.md)

