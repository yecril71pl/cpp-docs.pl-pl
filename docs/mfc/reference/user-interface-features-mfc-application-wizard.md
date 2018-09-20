---
title: Funkcje interfejsu użytkownika, Kreator aplikacji MFC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.exe.ui
dev_langs:
- C++
helpviewer_keywords:
- MFC Application Wizard, user interface features
ms.assetid: 59e7b829-a665-42eb-be23-3f2a36eb2dad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e18cc1f57bbbeb004fcbfc98f3671e29595f1329
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415138"
---
# <a name="user-interface-features-mfc-application-wizard"></a>Funkcje interfejsu użytkownika, kreator aplikacji MFC

W tym temacie opisano opcje, które można użyć, aby określić wygląd aplikacji. Funkcje interfejsu użytkownika dostępnych dla Twojego projektu są zależne od typu aplikacji określony w [typ aplikacji, Kreator aplikacji MFC](../../mfc/reference/application-type-mfc-application-wizard.md) strony Kreatora aplikacji MFC. Na przykład w przypadku tworzenia aplikacji interfejsu pojedynczego dokumentu nie można dodać style ramki podrzędnej.

- **Style ramki głównej**

   Ustawia funkcje ramki okna głównego aplikacji.

   |Opcja|Opis|
   |------------|-----------------|
   |**Grubą ramą**|Tworzy okno które ma granicę z ustalanym. Domyślnie.|
   |**Minimalizuj okno**|Zawiera pole minimalizacji w oknie głównym ramki. Domyślnie.|
   |**Maksymalizuj okno**|Zawiera pole maksymalizacji w oknie głównym ramki. Domyślnie.|
   |**Zminimalizowany**|Zostanie otwarty w oknie głównym ramki jako ikona.|
   |**Zmaksymalizowany**|Zostanie otwarty w oknie głównym ramki do pełnego rozmiaru ekranu.|
   |**Menu systemowe**|Zawiera menu systemowe w oknie głównym ramki. Domyślnie.|
   |**Pole informacji**|Obejmuje **o** pole dla aplikacji. Użytkownik ma dostęp do tego pola z aplikacji **pomocy** menu. Domyślnie i nie będzie zmieniana dopiero po wybraniu **oparte o okna dialogowe**w [typ aplikacji, Kreator aplikacji MFC](../../mfc/reference/application-type-mfc-application-wizard.md) strony.<br /><br /> **Uwaga** zwykle niedostępne opcja wskazuje, że Kreator nie dotyczy opcji projektu, czy pole wyboru niedostępności elementu lub odznaczane. W takim przypadku Kreator zawsze dodaje **o** pole do projektu, chyba że określono projektu jako oparte o okna dialogowe, a następnie usuń zaznaczenie pola.|
   |**Pasek stanu początkowego**|Dodaje pasek stanu aplikacji. Na pasku stanu zawiera automatyczne wskaźniki klawiatury włączony klawisz CAPS LOCK i NUM LOCK, SCROLL LOCK kluczy i wiersz wiadomości, która wyświetla Pomoc ciągi dla polecenia menu i paska narzędzi przycisków. Kliknięcie tej opcji dodaje także polecenia menu, aby wyświetlić lub ukryć pasek stanu. Domyślnie aplikacja ma pasek stanu. Niedostępne dla typów aplikacji oparta na oknach dialogowych.|
   |**Podziel okno**|Zawiera pasek podziału. Pasek podziału rozdziela widokach głównych aplikacji. W wielu dokumentów (MDI) aplikację z interfejsem okno klienta ramki podrzędnej MDI jest oknem podziału, oraz w aplikacji interfejsu (SDI) pojedynczego dokumentu oraz wielu aplikacji najwyższego poziomu dokumentu głównej ramki okna klienta okna rozdzielacza. Niedostępne dla typów aplikacji oparta na oknach dialogowych.|

- **Style ramki podrzędnej**

   Określa wygląd i początkowy stan ramki podrzędne w aplikacji. Style ramki podrzędnej są dostępne tylko w aplikacji MDI.

   |Opcja|Opis|
   |------------|-----------------|
   |**Pole minimalizacji podrzędne**|Określa, czy okno podrzędne znajduje się przycisk Minimalizuj (domyślnie włączone).|
   |**Pole maksymalizacji podrzędne**|Określa, czy okno podrzędne znajduje się przycisk Maksymalizuj (domyślnie włączone).|
   |**Zmaksymalizowane podrzędne**|Określa, czy okno podrzędne początkowo jest zmaksymalizowane, ustawiając cs.style Flaga WS_MAXIMIZE w [PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow) funkcji składowej typu `CChildFrame`.|

- **Paski poleceń (menu narzędzi/wstążki)**

   Wskazuje, czy aplikacja zawiera menu, paski narzędzi lub Wstążkę. Nie jest dostępna dla aplikacji oparta na oknach dialogowych.

   |Opcja|Opis|
   |------------|-----------------|
   |**Użyj klasycznego menu**|Określa, że aplikacja zawiera menu klasyczne, niewizualnych.|
   |**Użyj klasycznego, dokującego paska narzędzi**|Dodaje standardowy pasek narzędzi Windows do aplikacji. Pasek narzędzi zawiera przyciski do tworzenia nowego dokumentu. Otwieranie i zapisywanie plików dokumentów. Wycinanie, kopiowanie, wklejanie lub drukowanie tekstu. i trybu pomocy. Włączenie tej opcji dodaje także polecenia menu, aby wyświetlić lub ukryć pasek narzędzi.|
   |**Użyj paska narzędzi w stylu przeglądarki**|Dodaje pasek narzędzi w stylu Eksploratora Internet do aplikacji.|
   |**Użyj paska menu i paska narzędzi**|Wskazuje, że aplikacja zawiera pasek przeciąganego menu i paska narzędzi.|
   |**Paski narzędzi zdefiniowane przez użytkownika i obrazy**|Umożliwia to użytkownikowi dostosowywanie paska narzędzi i paska narzędzi obrazów w czasie wykonywania.|
   |**Zachowanie menu spersonalizowanego**|Określa, czy menu zawiera pełną listę elementów, po otwarciu lub jeśli zawiera polecenia, używanych przez tego użytkownika najczęściej.|
   |**Użyj wstążki**|Używa wstążki Office 2007 podobne w aplikacji, zamiast paska menu lub paska narzędzi.|

- **Tytuł okna dialogowego**

   Aby uzyskać [klasa CDialog](../../mfc/reference/cdialog-class.md)— aplikacje oparte na tylko ten tytuł pojawi się na pasku tytułu okna dialogowego. Aby edytować tego pola, należy najpierw wybrać **oparte o okna dialogowe** opcji w obszarze **typ aplikacji**. Aby uzyskać więcej informacji, zobacz [typ aplikacji, Kreator aplikacji MFC](../../mfc/reference/application-type-mfc-application-wizard.md).

## <a name="see-also"></a>Zobacz też

[Kreator aplikacji MFC](../../mfc/reference/mfc-application-wizard.md)

