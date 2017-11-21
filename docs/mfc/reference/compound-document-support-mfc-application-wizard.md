---
title: "Obsługa dokumentów złożonych, Kreator aplikacji MFC | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.appwiz.mfc.exe.compdoc
dev_langs: C++
ms.assetid: 42e1af83-12c4-438d-92eb-13835afdb148
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 952f27b0c6717d23395453e5159e125370a76804
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compound-document-support-mfc-application-wizard"></a>Obsługa dokumentów złożonych, kreator aplikacji MFC
Na tej stronie Kreatora aplikacji MFC wskazują, do jakiego poziomu aplikacji obsługuje złożone i aktywny dokument. Aplikacja musi obsługiwać architektury dokument/widok do obsługi dokumentów złożonych i szablonów dokumentów.  
  
 Domyślnie ta aplikacja zawiera Brak obsługi dokumentów złożonych. Jeśli akceptujesz to ustawienie domyślne, używana aplikacja nie obsługuje dokumenty aktywne lub pliki złożone.  
  
 **Obsługa dokumentów złożonych**  
 Określa, czy aplikacja udostępnia obsługę kontenera i obsługi serwera. Aby uzyskać więcej informacji dotyczących tego zakresu zobacz:  
  
-   [Kontenery: Implementowanie kontenera](../../mfc/containers-implementing-a-container.md)  
  
-   [Serwery: Implementowanie serwera](../../mfc/servers-implementing-a-server.md)  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Brak**|Wskazuje brak obsługi dla obiekt łączenie i osadzanie (OLE). Domyślnie Kreator aplikacji tworzy aplikację bez obsługi ActiveX.|  
|**Kontener**|Zawiera obiekty połączone i osadzone.|  
|**Mini serwer**|Wskazuje, aplikacja może utworzyć obiektów i zarządzanie nimi złożonego dokumentu. Należy pamiętać, że nie można uruchomić mini serwery autonomiczne i obsługują tylko elementy osadzone.|  
|**Pełny serwer**|Wskazuje, aplikacja może utworzyć obiektów i zarządzanie nimi złożonego dokumentu. Można uruchomić, autonomicznego i pomocy technicznej zarówno połączone i osadzone elementy są pełne serwery.|  
|**Kontener/pełny serwer**|Wskazuje, że aplikacja może być zarówno kontener, jak i serwera. Kontener jest aplikacja, która można zastosować elementy osadzone lub połączone w swoich własnych dokumentów. Serwer jest aplikacja, która może utworzyć elementy automatyzacji do użycia przez aplikacje kontenera.|  
  
 **Dodatkowe opcje**  
 Wskazuje, czy aplikacja obsługuje dokumenty aktywne. Zobacz [dokumenty aktywne](../../mfc/active-documents.md) Aby uzyskać więcej informacji dotyczących tej funkcji.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Serwer dokumentów aktywnych**|Wskazuje aplikacji można utworzyć i zarządzać nimi dokumenty aktywne. Jeśli wybierzesz tę opcję, należy określić rozszerzenie pliku dla dokumentów aktywnych serwera w **rozszerzenie pliku** polu [ciągi szablonu dokumentu](../../mfc/reference/document-template-strings-mfc-application-wizard.md) stronie kreatora. Zobacz [serwery dokumentów aktywnych](../../mfc/active-document-servers.md) Aby uzyskać więcej informacji.|  
|**Kontener dokumentów aktywnych**|Wskazuje, że aplikacja może zawierać aktywne dokumenty w swojej ramce. Dokumenty aktywne mogą obejmować na przykład dokumentów programu Internet Explorer lub dokumenty pakietu Office, takich jak pliki programu Microsoft Word lub arkuszy programu Excel. Zobacz [zawieranie dokumentów aktywnych](../../mfc/active-document-containment.md) Aby uzyskać więcej informacji.|  
|**Obsługa pliki złożone**|Nie serializować aplikacji kontenera dokumentów w formacie pliku złożone. Ta opcja wymusza ładowanie całego pliku zawierające obiekty do pamięci. Zapisuje przyrostowe do poszczególnych obiektów nie są dostępne. Jeśli jeden obiekt jest zmienione, a następnie zapisać, wszystkie obiekty w pliku są zapisywane.|  
  
## <a name="see-also"></a>Zobacz też  
 [Kreator aplikacji MFC](../../mfc/reference/mfc-application-wizard.md)

