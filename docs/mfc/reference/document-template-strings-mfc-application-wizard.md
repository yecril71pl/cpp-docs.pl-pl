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
ms.openlocfilehash: a2b1e30ac1e4381cdcd80eddd7fdd4ea27bde5a4
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45700573"
---
# <a name="document-template-strings-mfc-application-wizard"></a>Ciągi szablonu dokumentu, kreator aplikacji MFC
Na tej stronie Kreatora aplikacji MFC Podaj lub zawęzić poniższych opcji, aby ułatwić zarządzanie dokumentami i lokalizacji. Ciągi szablonu dokumentu są dostępne dla aplikacji, które zawierają **Obsługa architektury dokument/widok** w [typ aplikacji](../../mfc/reference/application-type-mfc-application-wizard.md). Nie są one dostępne dla okien dialogowych. Ponieważ większość ciągi szablonu dokumentu są widoczne i używane przez użytkowników aplikacji, są one zlokalizowane w **język zasobów** czcionką **typ aplikacji** strony kreatora.  
  
- **Niezlokalizowanej ciągów**

   Ma zastosowanie do aplikacji, które tworzą dokumentów użytkownika. Użytkownicy mogą otworzyć, drukowanie i zapisywanie dokumentów więcej łatwo Jeśli podasz rozszerzenie pliku i identyfikator typu pliku Te elementy nie są lokalizowane, ponieważ są one używane przez system, a nie przez użytkownika.  
  
   |Opcja|Opis|  
   |------------|-----------------|  
   |**Rozszerzenie pliku**|Określa rozszerzenie pliku, skojarzone z dokumentów, które użytkownik zapisuje w przypadku korzystania z aplikacji. Na przykład jeśli element Widget nosi nazwę projektu, możesz nazwać .wgt rozszerzenia pliku. (Po wprowadzeniu rozszerzenie pliku, nie dołączaj okres.)<br /><br /> Jeśli podasz rozszerzenie pliku, programu Explorer można wydrukować dokumentów aplikacji bez uruchamiania aplikacji, gdy użytkownik porzuca ikony dokumentu na ikonie drukarki.<br /><br /> Jeśli rozszerzenie nie jest określony, użytkownik musi określić rozszerzenie pliku, podczas zapisywania plików. Kreator nie zapewnia domyślne rozszerzenie pliku.|  
   |**Identyfikator typu pliku**|Ustawia etykietę dla danego typu dokumentu w rejestrze systemowym.|  
  
- **Zlokalizowane ciągi**

   Tworzy ciągi skojarzone z aplikacji i dokumentu, który odczytu i używane przez użytkowników aplikacji, dzięki czemu są zlokalizowane ciągi.  
  
   |Opcja|Opis|  
   |------------|-----------------|  
   |**Język**|Określa język, w którym ciągi są wyświetlane dla wszystkich pól w obszarze **zlokalizowane ciągi**. Aby zmienić wartości w tym polu, wybierz odpowiedni język, w obszarze **język zasobów** w [typ aplikacji](../../mfc/reference/application-type-mfc-application-wizard.md) strony Kreatora aplikacji MFC.|  
   |**Podpis ramki głównej**|Określa tekst wyświetlany u góry strony ramki głównego aplikacji. Domyślnie nazwa projektu.|  
   |**Nazwa typu dokumentu**|Identyfikuje typ dokumentu, w którym mogą być grupowane dokumentu aplikacji. Domyślnie nazwa projektu. Zmienianie domyślnego nie powoduje zmiany innych opcji, w tym oknie dialogowym.|  
   |**Nazwa filtru**|Ustawia nazwę, którą można wskazać użytkowników, do wyszukiwania plików tego typu pliku. Ta opcja jest dostępna z **pliki typu** i **Zapisz jako typ** opcje w standardowych Windows **Otwórz** i **Zapisz jako** okien dialogowych. Przez domyślny, nazwę projektu oraz pliki, a następnie rozszerzenia w **rozszerzenie pliku**. Na przykład, jeśli projekt nosi nazwę elementu Widget i rozszerzenie pliku jest .wgt **nazwy filtru** jest element Widget plików (*.wgt) domyślnie.|  
   |**Krótka nazwa nowego pliku**|Ustawia nazwę w standardowych Windows **New** okno dialogowe, jeśli istnieje więcej niż jeden nowy szablon dokumentu. Jeśli aplikacja jest [serwer automatyzacji](../../mfc/automation-servers.md), ta nazwa jest używana jako krótka nazwa obiektu automatyzacji. Domyślnie nazwa projektu.|  
   |**Długa nazwa typu pliku**|Ustawia nazwę typu pliku w rejestrze systemowym. Jeśli aplikacja serwera automatyzacji, ta nazwa jest używana jako długa nazwa obiektu automatyzacji. Domyślnie nazwa projektu plus. Dokument.|  
  
## <a name="see-also"></a>Zobacz też  
 [Kreator aplikacji MFC](../../mfc/reference/mfc-application-wizard.md)

