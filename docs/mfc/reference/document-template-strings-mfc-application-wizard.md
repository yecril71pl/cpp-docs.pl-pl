---
title: Ciągi szablonu dokumentu, Kreator aplikacji MFC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.exe.doctemp
dev_langs:
- C++
helpviewer_keywords:
- MFC Application Wizard, document template strings
ms.assetid: 8109f662-3182-4682-977a-2503321c678a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 32d684d7b9b5f8057893d79b864be7b6d9b512fc
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122199"
---
# <a name="document-template-strings-mfc-application-wizard"></a>Ciągi szablonu dokumentu, kreator aplikacji MFC
Na tej stronie Kreatora aplikacji MFC Podaj lub Popraw następujące opcje ułatwiające zarządzanie dokumentami i lokalizacja. Ciągi szablonu dokumentu są dostępne dla aplikacji, które obejmują **wsparcie dla architektury dokument/widok** w [typu aplikacji](../../mfc/reference/application-type-mfc-application-wizard.md). Nie są one dostępne w oknach dialogowych. Ponieważ większość ciągi szablonu dokumentu są widoczne i używane przez użytkowników aplikacji, są zlokalizowane w **języka zasobu** wskazane **typu aplikacji** stronie kreatora.  
  
 **Niezlokalizowanej ciągów**  
 Dotyczy aplikacji, które tworzą dokumenty użytkowników. Użytkownicy mogą otworzyć, drukowania i zapisywać dokumenty więcej łatwo Jeśli należy podać rozszerzenie pliku i identyfikator typu pliku Te elementy nie są zlokalizowane, ponieważ są one używane przez system, a nie przez użytkownika.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Rozszerzenie pliku**|Określa rozszerzenie pliku skojarzone z dokumentów, które użytkownik zapisuje w przypadku korzystania z aplikacji. Na przykład w projekcie ma nazwę elementu Widget, można nazwę .wgt rozszerzenia pliku. (Po wprowadzeniu rozszerzenie pliku nie dołączaj okres.)<br /><br /> Należy podać rozszerzenie pliku, Eksploratora wydrukować dokumentów aplikacji bez konieczności uruchamiania aplikacji, gdy użytkownik porzuca ikonę dokumentu ikonę drukarki.<br /><br /> Jeśli nie określisz rozszerzenie, podczas zapisywania plików należy podać rozszerzenie pliku. Kreator nie zapewnia domyślne rozszerzenie pliku.|  
|**Identyfikator typu pliku**|Ustawia etykietę dla danego typu dokumentu w rejestrze systemu.|  
  
 **Zlokalizowanych ciągów**  
 Tworzy ciągi skojarzone z aplikacją i dokument do odczytu i używane przez użytkowników aplikacji, więc są zlokalizowane ciągi.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Język**|Określa język, w którym ciągów są wyświetlane dla wszystkich pól w obszarze **zlokalizowane ciągi**. Aby zmienić wartość w tym polu, wybierz odpowiedni język, w obszarze **języka zasobu** w [typu aplikacji](../../mfc/reference/application-type-mfc-application-wizard.md) Kreatora aplikacji MFC.|  
|**Podpis ramki głównej**|Ustawia tekst znajdujący się w górnej części głównej ramki aplikacji. Domyślnie nazwa projektu.|  
|**Nazwa typu dokumentu**|Określa typ dokumentu, pod którym można grupować dokumentów aplikacji. Domyślnie nazwa projektu. Wartość domyślna nie zmiana dowolnych innych opcji, w tym oknie dialogowym.|  
|**Nazwa filtru**|Ustawia nazwę, którą można wskazać użytkowników, można znaleźć plików tego typu pliku. Ta opcja jest dostępna z **pliki typu** i **Zapisz jako typ** opcje w oknach standardowe **Otwórz** i **Zapisz jako** okien dialogowych. Przez domyślną nazwę projektu i plików, a następnie rozszerzenia zawarte w **rozszerzenie pliku**. Na przykład, jeśli projekt nosi nazwę elementu Widget i rozszerzenie pliku jest .wgt **nazwę filtru** jest domyślnie pliki Widget (*.wgt).|  
|**Krótka nazwa nowego pliku**|Ustawia nazwę znajdujących się w standardowych oknach **nowy** okno dialogowe, jeśli istnieje więcej niż jeden nowy szablon dokumentu. Jeśli aplikacja jest [serwer automatyzacji](../../mfc/automation-servers.md), ta nazwa jest używana jako krótka nazwa obiektu automatyzacji. Domyślnie nazwa projektu.|  
|**Długa nazwa typu pliku**|Ustawia nazwę typu pliku w rejestrze systemu. Jeśli aplikacja serwera automatyzacji, ta nazwa jest używana jako długa nazwa obiektu automatyzacji. Domyślnie nazwa projektu plus. Dokument.|  
  
## <a name="see-also"></a>Zobacz też  
 [Kreator aplikacji MFC](../../mfc/reference/mfc-application-wizard.md)

