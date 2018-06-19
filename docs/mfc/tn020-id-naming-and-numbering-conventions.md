---
title: 'TN020: Identyfikator nazewnictwa i numerowania identyfikatorów konwencje | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.id
dev_langs:
- C++
helpviewer_keywords:
- TN020
- resource identifiers, naming and numbering
- resource identifiers
ms.assetid: aecbd2cf-68b3-47f6-ae21-b1f507917245
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 17b27b4cfc1b624c9c12138154a660951a0f2a13
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33384114"
---
# <a name="tn020-id-naming-and-numbering-conventions"></a>TN020: konwencje nazewnictwa i numerowania identyfikatorów
Ta uwaga opisuje identyfikator nazewnictwa i numerowania Konwencji MFC 2.0 korzysta z zasobów, polecenia, parametry, formantów i okien podrzędnych.  
  
 Nazewnictwa MFC identyfikator i numerowanie konwencje powinny spełniać następujące wymagania:  
  
-   Podaj spójne standard nazewnictwa identyfikator używany w aplikacjach MFC, które są obsługiwane przez Edytor zasobów programu Visual C++ i biblioteki MFC. To ułatwia programisty interpretować typu i pochodzenia zasobu z jego identyfikator.  
  
-   Wyróżnianie silne Relacja 1 do 1 między niektórych typów identyfikatorów.  
  
-   Ze standardami już powszechnie używany do nadawania nazw identyfikatorów w systemie Windows.  
  
-   Partycja numerowanie identyfikator miejsca. Numery identyfikacyjne można przypisać programisty, MFC, Windows i edytować Visual C++ zasobów. Partycjonowanie odpowiednie pomoże uniknąć duplikowania identyfikatorów.  
  
## <a name="the-id-prefix-naming-convention"></a>Konwencja nazewnictwa prefiks Identyfikatora  
 Kilka typów identyfikatorów może wystąpić w aplikacji. Konwencja nazewnictwa MFC identyfikator definiuje różne prefiksy dla różnych typów zasobów.  
  
 Prefiks "IDR_" jest używane w MFC wskazuje identyfikator zasobu, którego dotyczy wiele typów zasobów. Na przykład dla okno ramowe danego MFC używa tego samego prefiksu "IDR_" wskazująca zasobu menu, akceleratora, ciągu i ikona. W poniższej tabeli przedstawiono różne prefiksy i ich użycia:  
  
|Prefiks|Zastosowanie|  
|------------|---------|  
|IDR_|Dla wielu typów zasobów (głównie używane w menu, akceleratory i taśmy).|  
|IDD_|Okno dialogowe szablonu zasobów (na przykład IDD_DIALOG1).|  
|IDC_|Dla zasobów kursora.|  
|IDI_|Ikona zasobów.|  
|IDB_|Dla zasobów mapy bitowej.|  
|IDS_|Dla zasobów ciągu.|  
  
 W ramach zasób okna DIALOGOWEGO MFC z konwencjami te:  
  
|Prefiks lub etykiety|Zastosowanie|  
|---------------------|---------|  
|IDOK, IDCANCEL|Dla przycisku polecenia standardowych identyfikatorów.|  
|IDC_|Dla innych formantów okna dialogowego.|  
  
 Prefiks "IDC_" służy także do kursorów. Ten konflikt nazw nie jest zazwyczaj problem ponieważ Typowa aplikacja będzie mieć kilka kursory i wiele formantów okna dialogowego.  
  
 W ramach zasobu menu MFC z konwencjami te:  
  
|Prefiks|Zastosowanie|  
|------------|---------|  
|IDM_|Dla elementów menu, które nie korzystają z architektury polecenia MFC.|  
|ID_|Dla polecenia menu, korzystających z architektury polecenia MFC.|  
  
 Polecenia, które należy wykonać polecenie architekturę MFC musi mieć `ON_COMMAND` polecenia Obsługa i może zawierać `ON_UPDATE_COMMAND_UI` obsługi. Jeśli te programy obsługi poleceń zgodna z architekturą polecenia MFC, będą one działać poprawnie Określa, czy są powiązane z polecenia menu, przycisk paska narzędzi lub przycisk paska dialogowego. Tego samego prefiksu "ID_" służy także do menu ciąg monitu, który jest wyświetlany na pasku komunikatów programu. Większość elementów menu w aplikacji powinny być zgodne z konwencjami polecenia MFC. Wszystkie standardowe identyfikatory poleceń (na przykład `ID_FILE_NEW`) wykonaj tę Konwencję.  
  
 MFC używa również "IDP_" jako specjalna forma ciągów (zamiast "IDS_"). Ciągi z prefiksem "IDP_" są monity, czyli ciągów używanych w polach komunikatu. Ciągi "IDP_" może zawierać "%1" i "%2" jako symbole zastępcze ciągów określany przez program. "IDP_" ciągi, które są zwykle skojarzone z nimi tematy pomocy, a nie zawierają ciągi "IDS_". Zawsze są zlokalizowane ciągi "IDP_" i nie mogą być zlokalizowane ciągi "IDS_".  
  
 Biblioteki MFC używa również prefiksu "IDW_" jako specjalna forma kontroli identyfikatorów (zamiast "IDC_"). Te identyfikatory są przypisane do podrzędnych systemu windows, takich jak widoki i rozdzielaczy przez klasy framework. Identyfikatory implementacji MFC nazwy są poprzedzone ciągiem "AFX_".  
  
## <a name="the-id-numbering-convention"></a>Konwencja numerowanie identyfikator  
 Poniższa tabela zawiera listę prawidłowych zakresów identyfikatorów określonych typów. Niektóre limity są limity implementacji technicznej, a inne są konwencje, które są zaprojektowane, aby zapobiec Twoje nazwy kolizji z wstępnie zdefiniowane identyfikatory systemu Windows lub MFC domyślnej implementacji.  
  
 Zdecydowanie zaleca się zdefiniowania wszystkich identyfikatorów wewnątrz zalecane zakresów. Dolna granica tych zakresów wynosi 1, ponieważ 0 nie jest używany. Zaleca się używać konwencji typowe i używać 100 lub 101 jako pierwszy identyfikator.  
  
|Prefiks|Typ zasobu|Prawidłowy zakres|  
|------------|-------------------|-----------------|  
|IDR_|wiele|od 1 do 0x6FFF|  
|IDD_|szablony okna dialogowego|od 1 do 0x6FFF|  
|IDB_ IDC_, IDI_,|kursory, ikony, mapy bitowe|od 1 do 0x6FFF|  
|IDS_, IDP_|Parametry ogólne|od 1 do 0x7FFF|  
|ID_|polecenia|0x8000 za pośrednictwem 0xDFFF|  
|IDC_|kontrolki|8 do 0xDFFF|  
  
 Ze względu na tych limitów zasięgu:  
  
-   Konwencja nie jest używana wartość Identyfikatora równą 0.  
  
-   Ograniczenia dotyczące wdrażania systemu Windows ograniczyć true zasobów identyfikatorów jest mniejsza niż lub równa 0x7FFF.  
  
-   MFC framework wewnętrzny rezerwuje tych zakresów:  
  
    -   0x7000 za pośrednictwem 0x7FFF (zobacz afxres.h)  
  
    -   0xE000 za pośrednictwem 0xEFFF (zobacz afxres.h)  
  
    -   16000 za pośrednictwem 18000 (zobacz afxribbonres.h)  
  
     Te zakresy mogą ulec zmianie w przyszłych implementacji MFC.  
  
-   Kilka poleceń systemu Windows użyj zakresu 0xF000 do 0xFFFF.  
  
-   Identyfikatory sterowania od 1 do 7 są zastrzeżone dla formantów standardowych, takich jak IDOK i IDCANCEL.  
  
-   Zakres 0x8000 do 0xFFFF dla ciągów jest zarezerwowana dla monitów menu poleceń.  
  
## <a name="see-also"></a>Zobacz też  
 [Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)   
 [Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

