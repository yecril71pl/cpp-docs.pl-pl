---
title: Obsługa dokumentów złożonych, kreator aplikacji MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.compdoc
ms.assetid: 42e1af83-12c4-438d-92eb-13835afdb148
ms.openlocfilehash: b2ff4f312132b690223f124fd8790d0e2c172b7f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57289679"
---
# <a name="compound-document-support-mfc-application-wizard"></a>Obsługa dokumentów złożonych, kreator aplikacji MFC

Na tej stronie Kreatora aplikacji MFC wskazuje, jaki poziom aplikacji zapewnia obsługę złożone i aktywnego dokumentu. Aplikacja musi obsługiwać architektury dokument/widok do obsługi złożonych dokumentów i szablonów dokumentów.

Domyślnie ta aplikacja zawiera nie obsługuje dokumentów złożonych. Jeśli zdecydujesz się zaakceptować ustawienie domyślne, aplikacja nie może obsługiwać dokumenty aktywne lub pliki złożone.

- **Obsługa dokumentów złożonych**

  Określa, czy aplikacja udostępnia obsługi kontenerów i pomoc techniczna dotycząca serwera. Aby uzyskać więcej informacji na temat tego obszaru zobacz:

  - [Kontenery: Implementowanie kontenera](../../mfc/containers-implementing-a-container.md)

  - [Serwery: Implementowanie serwera](../../mfc/servers-implementing-a-server.md)

  |Opcja|Opis|
  |------------|-----------------|
  |**Brak**|Wskazuje brak obsługi łączenie i osadzanie (OLE). Domyślnie Kreator aplikacji tworzy aplikację bez obsługi ActiveX.|
  |**Kontener**|Zawiera obiekty połączone i osadzone.|
  |**Mini serwer**|Wskazuje aplikacji można tworzyć i zarządzać obiektami w dokumencie złożonym. Należy zauważyć, że nie można uruchomić miniserwery autonomiczne i obsługują tylko elementów osadzonych.|
  |**Pełny serwer**|Wskazuje aplikacji można tworzyć i zarządzać obiektami w dokumencie złożonym. Pełnych będą mogli uruchamiać autonomicznego i pomocy technicznej, obie połączone i osadzone elementy.|
  |**Kontener/pełny serwer**|Wskazuje, że aplikacja może być zarówno kontenera, jak i serwera. Kontener jest aplikacja, która można zastosować osadzony lub połączony elementy w swoich własnych dokumentów. Serwer jest aplikacja, która można tworzyć elementy automatyzacji do użytku przez aplikacje kontenera.|

- **Dodatkowe opcje**

  Wskazuje, czy aplikacja obsługuje dokumenty aktywne. Zobacz [dokumenty aktywne](../../mfc/active-documents.md) Aby uzyskać więcej informacji na temat tej funkcji.

  |Opcja|Opis|
  |------------|-----------------|
  |**Serwer aktywnego dokumentu**|Wskazuje aplikacji można tworzyć i zarządzać dokumenty aktywne. Jeśli wybierzesz tę opcję, należy określić rozszerzenie pliku dla serwera aktywnego dokumentu w **rozszerzenie pliku** pole w [ciągi szablonu dokumentu](../../mfc/reference/document-template-strings-mfc-application-wizard.md) strony kreatora. Zobacz [serwery dokumentów aktywnych](../../mfc/active-document-servers.md) Aby uzyskać więcej informacji.|
  |**Kontener dokumentów aktywnych**|Wskazuje, że aplikacja może zawierać dokumenty aktywne wewnątrz ramki. Dokumenty aktywne mogą obejmować na przykład dokumentów programu Internet Explorer lub dokumentów pakietu Office, takie jak pliki programu Microsoft Word lub arkuszy kalkulacyjnych programu Excel. Zobacz [zawieranie dokumentów aktywnych](../../mfc/active-document-containment.md) Aby uzyskać więcej informacji.|
  |**Obsługa plików złożonych**|Nie serializować aplikacji kontenera dokumentów przy użyciu formatu pliku złożone. Ta opcja wymusza ładowanie cały plik zawierający obiekty do pamięci. Zapisuje przyrostowe na poszczególne obiekty nie są dostępne. Jeśli jeden obiekt zmienione, a następnie zapisany, wszystkie obiekty w pliku są zapisywane.|

## <a name="see-also"></a>Zobacz także

[Kreator aplikacji MFC](../../mfc/reference/mfc-application-wizard.md)
