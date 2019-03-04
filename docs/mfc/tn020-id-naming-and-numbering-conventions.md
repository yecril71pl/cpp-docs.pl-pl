---
title: 'TN020: Konwencje identyfikator nazewnictwa i numerowania'
ms.date: 11/04/2016
f1_keywords:
- vc.id
helpviewer_keywords:
- TN020
- resource identifiers, naming and numbering
- resource identifiers
ms.assetid: aecbd2cf-68b3-47f6-ae21-b1f507917245
ms.openlocfilehash: f1cd44ed448cc4c0fc60d490a613f0ad91071376
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57267397"
---
# <a name="tn020-id-naming-and-numbering-conventions"></a>TN020: Konwencje identyfikator nazewnictwa i numerowania

Ta uwaga opisuje identyfikator nazewnictwa i numerowania Konwencji MFC 2.0 używa zasobów, polecenia, ciągów, formantów i okien podrzędnych.

Konwencje nazewnictwa MFC identyfikator i numerowania powinny spełniać następujące wymagania:

- Zapewnia spójny standard nazewnictwa identyfikator używany w bibliotece MFC i aplikacji MFC, które są obsługiwane przez Edytor zasobów Visual C++. Umożliwia to łatwiejsze do programisty należy interpretować typ i pochodzenia zasobu z jego identyfikatora.

- Wyróżnianie silne Relacja 1 do 1 niektórych typów identyfikatorów.

- Zgodne ze standardami już powszechnie używanych nazewnictwa identyfikatorów w Windows.

- Partycja numerowanie identyfikator miejsca. Programista, MFC, Windows i zasoby były edytowane środowisko Visual C++ można przypisać numery identyfikatorów. Właściwe partycjonowanie może pomóc uniknąć duplikowania numery identyfikatorów.

## <a name="the-id-prefix-naming-convention"></a>Konwencja nazewnictwa prefiks Identyfikatora

Kilka typów identyfikatorów może wystąpić w aplikacji. Konwencja nazewnictwa MFC identyfikator definiuje różne prefiksy dla różnych typów zasobów.

MFC używa prefiksu "IDR_", aby wskazać identyfikator zasobu, który ma zastosowanie do wielu typów zasobów. Na przykład dla danej ramki okna, MFC używa tego samego prefiksu "IDR_" Aby wskazać zasobu menu, akcelerator, parametry i ikona. W poniższej tabeli przedstawiono różne prefiksy i ich użycia:

|Prefiks|Zastosowanie|
|------------|---------|
|IDR_|Dla wielu typów zasobów (głównie używane do menu, akceleratory i wstążki).|
|IDD_|Okno dialogowe szablonu zasobów (na przykład IDD_DIALOG1).|
|IDC_|Dla zasobów kursora.|
|IDI_|Ikona zasobów.|
|IDB_|Dla zasobów mapy bitowej.|
|IDS_|Aby uzyskać zasoby w postaci ciągów.|

W ramach zasobu okna DIALOGOWEGO MFC jest zgodna z konwencjami te:

|Prefiks lub etykieta|Zastosowanie|
|---------------------|---------|
|IDOK, IDCANCEL|Standardowa przycisku wypychania identyfikatorów.|
|IDC_|W przypadku innych formantów okna dialogowego.|

Prefiks "IDC_" służy do kursorów. Ten konflikt nazw nie jest zazwyczaj problemem ponieważ Typowa aplikacja będzie mieć kilka kursorów i wiele formantów okna dialogowego.

W ramach zasobu menu MFC jest zgodna z konwencjami te:

|Prefiks|Zastosowanie|
|------------|---------|
|IDM_|Dla elementów menu, które nie korzystają z architektury polecenia MFC.|
|ID_|Dla polecenia menu, które używają architektury polecenia MFC.|

Polecenia, postępuj zgodnie z architekturą polecenia MFC, które musi mieć procedurę obsługi poleceń ON_COMMAND i może mieć do obsługi ON_UPDATE_COMMAND_UI. Jeśli programy obsługi tych poleceń jest zgodna z architekturą polecenia MFC, one będzie działać prawidłowo tego, czy są one powiązane z polecenia menu, przycisk paska narzędzi lub przycisk paska dialogowego. Ten sam prefiks "ID_" służy do menu ciąg monitu, który jest wyświetlany na jego pasku komunikatów Centrum użytkowników. Większość elementów menu w aplikacji powinien być zgodny z konwencjami polecenia MFC. Wszystkie identyfikatory poleceń standardowych (na przykład id_file_new —) stosują taką Konwencję.

MFC używa również "IDP_" jako formą specjalistyczne ciągów (zamiast "IDS_"). Ciągi z prefiksem "IDP_" są monity, czyli ciągów używanych w polach wiadomości. Ciągi "IDP_" może zawierać "%1" i "%2" jako symbole zastępcze ciągów ustalone przez program. Ciągi "IDP_" mają zwykle tematów związanych z nimi, a nie obsługują ciągi "IDS_". Ciągi "IDP_" zawsze są lokalizowane i ciągów "IDS_" może nie być zlokalizowana.

Biblioteki MFC używa także prefiks "IDW_" jako formą specjalistyczne kontroli identyfikatorów (zamiast "IDC_"). Te identyfikatory są przypisywane do okien nadrzędnych, takich jak widoki i rozdzielaczy przez klasy framework. Identyfikatory implementacji MFC mają prefiks "AFX_".

## <a name="the-id-numbering-convention"></a>Konwencja numerowanie identyfikator

W poniższej tabeli wymieniono prawidłowe zakresy dla identyfikatorów określonych typów. Niektóre ograniczenia są limity implementacji technicznej, a inne są konwencje, które są przeznaczone do uniemożliwić kolizji z wstępnie zdefiniowane identyfikatory Windows lub MFC domyślnej implementacji swoim identyfikatorem.

Zdecydowanie zaleca się, że zdefiniowane wszystkie identyfikatory wewnątrz zalecane zakresy. Dolna granica tych zakresów to 1, ponieważ 0 nie jest używany. Zaleca się używać typową Konwencją i używać 100 lub 101 jako identyfikator pierwszego.

|Prefiks|Typ zasobu|Prawidłowy zakres|
|------------|-------------------|-----------------|
|IDR_|wiele|od 1 do 0x6FFF|
|IDD_|szablony okna dialogowego|od 1 do 0x6FFF|
|IDC_,IDI_,IDB_|kursory, ikony, mapy bitowe|od 1 do 0x6FFF|
|IDS_, IDP_|Parametry ogólne|od 1 do 0x7FFF|
|ID_|polecenia|0x8000 do 0xDFFF|
|IDC_|kontrolki|8 do 0xDFFF|

Przyczyny te limity zakres:

- Zgodnie z Konwencją nie jest używana wartość Identyfikatora równą 0.

- Ograniczenia wdrożenia Windows ograniczenia zasobów true identyfikatorów jest mniejsza niż lub równa 0x7FFF.

- Biblioteki MFC wewnętrzną strukturę rezerwuje tych zakresów:

  - 0x7000 za pośrednictwem 0x7FFF (patrz afxres.h)

  - 0xE000 za pośrednictwem 0xEFFF (patrz afxres.h)

  - 16000 za pośrednictwem 18000 (zobacz afxribbonres.h)

  Te zakresy mogą ulec zmianie w przyszłości implementacji MFC.

- Kilka poleceń systemu Windows użyj zakresu 0xF000 0xffff.

- Identyfikatory kontroli od 1 do 7 są zarezerwowane dla standardowych kontrolek, takich jak IDOK i IDCANCEL.

- Zakres 0x8000 0xFFFF dla ciągów jest zarezerwowana do menu monity dotyczące poleceń.

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
