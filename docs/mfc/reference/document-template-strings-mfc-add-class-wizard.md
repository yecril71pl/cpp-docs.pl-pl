---
title: "Ciągi szablonu dokumentu, Kreator dodawania klasy MFC | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.codewiz.class.mfc.simple.doctemp
dev_langs: C++
helpviewer_keywords: MFC Add Class Wizard, document control strings
ms.assetid: 14e1c834-5e79-4dbd-811f-ec8f0a9cdcb2
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3a9d37b1a886c28d267cd7a387317edce6bf7f3a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="document-template-strings-mfc-add-class-wizard"></a>Ciągi szablonu dokumentu, kreator dodawania klas MFC
Ta strona kreatora jest dostępna tylko dla klas spełniającego następujące kryteria:  
  
-   Projekt MFC obsługuje architekturę dokument/widok.  
  
-   Jest klasą bazową dla nowej klasy [CFormView](../../mfc/reference/cformview-class.md).  
  
-   Pole wyboru **opcję generowania zasobów** jest zaznaczony na **nazwy** sekcji [Kreator klas MFC](../../mfc/reference/mfc-add-class-wizard.md).  
  
 Kreator udostępnia wartości domyślne dla następujących wartości do formularzy widok projektu, zarządzania i lokalizacji. Ponieważ większość ciągi szablonu dokumentu są widoczne i używane przez użytkowników formularza, są zlokalizowane w **języka zasobu** wskazane [typy aplikacji](../../mfc/reference/application-type-mfc-application-wizard.md) Kreatora aplikacji MFC Podczas tworzenia projektu.  
  
> [!NOTE]
>  Kreator nie zapewnia automatycznego obsługę drukowania dla klasy wyprowadzone z `CFormView`.  
  
 Zobacz [szablony dokumentów i proces tworzenia dokumentu/widoku](../../mfc/document-templates-and-the-document-view-creation-process.md) uzyskać więcej informacji.  
  
## <a name="nonlocalized-strings"></a>Niezlokalizowanej ciągów  
 Dotyczy aplikacji, które tworzą dokumenty użytkowników. Użytkownicy mogą otworzyć i zapisywać dokumenty więcej łatwo Jeśli typ dokumentu ma rozszerzenie pliku i identyfikator typu pliku Te elementy nie są zlokalizowane, ponieważ są one używane przez system, a nie przez użytkownika.  
  
 **Rozszerzenie pliku**  
 Określa rozszerzenie pliku skojarzone z typem dokumentu dla tej aplikacji formularzy. Domyślne rozszerzenie pliku na podstawie nazwy klasy. Na przykład, jeśli nosi nazwę nowej klasy MFC **CWidget**, domyślnie jest rozszerzeniem. wid. Rozszerzenie pliku jest używany w pliku filtrów i **Otwórz** i **Zapisz jako** okien dialogowych.  
  
 Jeśli zmienisz rozszerzenie pliku, zmiana ta jest uwzględniana w **nazwę filtru** pole.  
  
> [!NOTE]
>  Jeśli zmienisz domyślne rozszerzenie pliku nie dołączaj okresu.  
  
 **Identyfikator typu pliku**  
 Ustawia etykietę dla danego typu dokumentu w rejestrze systemu.  
  
## <a name="localized-strings"></a>Zlokalizowanych ciągów  
 Tworzy ciągi skojarzone z formularzy i dokumentów, które są odczytywanie oraz używane przez użytkowników aplikacji, więc są zlokalizowane ciągi.  
  
 **Nazwa typu dokumentu**  
 Określa typ dokumentu, pod którym można grupować dokumentów aplikacji. Domyślnie jest on oparty na nazwę klasy. Na przykład, jeśli nosi nazwę nowej klasy MFC **CWidget**, domyślnie nazwa typu dokumentu jest elementu Widget. Wartość domyślna nie zmiana dowolnych innych opcji, w tym oknie dialogowym.  
  
 **Nazwa filtru**  
 Ustawia nazwę, która może wskazywać użytkownicy, można znaleźć plików określonego typu pliku. Ta opcja jest dostępna z **pliki typu** i **Zapisz jako typ** opcje w oknach standardowe **Otwórz** i **Zapisz jako** okien dialogowych. Domyślnie nazwa opiera się na nazwę projektu oraz pliki, a następnie przez rozszerzenie wskazanych w **rozszerzenie pliku**. Na przykład, jeśli projekt nosi nazwę elementu Widget i rozszerzenie pliku jest .wid **nazwę filtru** jest domyślnie pliki Widget (*.wid).  
  
 **Krótka nazwa nowego pliku**  
 Ustawia nazwę znajdujących się w standardowych oknach `New` okno dialogowe, jeśli projekt zawiera więcej niż jeden szablon dokumentu. Jeśli aplikacja jest [serwer automatyzacji](../../mfc/automation-servers.md), ta nazwa jest używana jako krótka nazwa obiektu automatyzacji. Domyślnie ta nazwa jest oparta na nazwę klasy.  
  
 **Długa nazwa typu pliku**  
 Ustawia nazwę typu pliku w rejestrze systemu. Jeśli aplikacja serwera automatyzacji, ta nazwa jest używana jako długa nazwa obiektu automatyzacji. Domyślnie ta nazwa opiera się na nazwę klasy plus. Dokument. Na przykład, jeśli nazwa klasy jest **CWidget**, **długa nazwa typu pliku** jest dokumentem elementu Widget.  
  
 **Klasy dokumentów**  
 Wskazuje klasa dokumentu typu projektu. Domyślnie ta klasa jest klasa dokumentu aplikacji głównej, wymienione w [Przejrzyj wygenerowane klasy](../../mfc/reference/generated-classes-mfc-application-wizard.md) Kreatora aplikacji MFC. Jeśli dodano inne klasy dokumentu w projekcie, możesz wybrać inną klasę dokumentu z listy.  
  
## <a name="see-also"></a>Zobacz też  
 [Kreator dodawania klasy MFC](../../mfc/reference/mfc-add-class-wizard.md)   
 [Klasy MFC](../../mfc/reference/adding-an-mfc-class.md)   
 [Dodawanie klasy](../../ide/adding-a-class-visual-cpp.md)
