---
title: "Architektura podglądu wydruku | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- print preview [MFC], process
- previewing printing
- print preview [MFC], architecture
- printing [MFC], print preview
- print preview [MFC], modifications to MFC
ms.assetid: 0efc87e6-ff8d-43c5-9d72-9b729a169115
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ffffa6c446487752974549f4a070cf8e86e91aea
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="print-preview-architecture"></a>Architektura podglądu wydruku
W tym artykule opisano, jak MFC framework implementuje funkcje podglądu wydruku. Tematy obejmują:  
  
-   [Proces podglądu wydruku](#_core_the_print_preview_process)  
  
-   [Modyfikowanie podglądu wydruku](#_core_modifying_print_preview)  
  
 Podgląd wydruku jest nieznacznie różnić się od ekranu i drukowanie, ponieważ zamiast bezpośrednio rysowania obrazu na urządzeniu, aplikacja musi symulować drukarki na ekranie. Aby to umożliwić, Microsoft Foundation Class Library definiuje specjalne (nieudokumentowanej) klasy pochodzącej od [klasa CDC](../mfc/reference/cdc-class.md)o nazwie **CPreviewDC**. Wszystkie `CDC` obiekty zawierają dwa konteksty urządzenia, ale zazwyczaj są identyczne. W **CPreviewDC** obiektu, są one różne: pierwszy reprezentuje drukarki jest symulowane, a druga — ekran, na którym dane wyjściowe nie są wyświetlane.  
  
##  <a name="_core_the_print_preview_process"></a>Proces podglądu wydruku  
 Gdy użytkownik wybierze polecenie Podgląd wydruku z **pliku** tworzy platformę menu **CPreviewDC** obiektu. Zawsze, gdy aplikacja wykonuje operację, która ustawia cech kontekstu urządzenia drukarki, platformę wykonuje także podobna operacja na ekranie kontekst urządzenia. Na przykład jeśli aplikacja wybiera czcionkę do drukowania, platformę wybiera czcionkę dla ekranu, która symuluje czcionka drukarki. Zawsze, gdy aplikacja będzie Wyślij dane wyjściowe do drukarki, platformę zamiast wysyła dane wyjściowe do ekranu.  
  
 Podgląd wydruku również różni się od drukowanie w kolejności, że każdy rysuje stron dokumentu. Podczas drukowania, platformę nadal wydruku pętlę aż wyrenderowaniu zakresu stron. Podczas podglądu wydruku jednej lub dwóch stronach są wyświetlane w dowolnym momencie, a następnie aplikacja oczekuje; nie dalsze strony są wyświetlane, dopóki użytkownik nie wykona. W podglądzie wydruku aplikacji musi również odpowiadać na `WM_PAINT` komunikaty, tak jak w zwykłym ekranu.  
  
 [CView::OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) funkcja jest wywoływana po wywołaniu trybu podglądu, dokładnie tak jak na początku zadania drukowania. [Cprintinfo — struktura](../mfc/reference/cprintinfo-structure.md) struktura przekazany do funkcji zawiera kilka elementów członkowskich wartości, których można ustawić, aby dopasować niektórych parametrów operacji podglądu wydruku. Na przykład można ustawić **m_nNumPreviewPages** element członkowski, aby określić, czy podglądu dokumentu w trybie jednej strony lub dwie strony.  
  
##  <a name="_core_modifying_print_preview"></a>Modyfikowanie podglądu wydruku  
 Zamiast łatwo można modyfikować działanie i wygląd podglądu wydruku na kilka sposobów. Na przykład możesz, między innymi:  
  
-   Spowodować, że okno podglądu wydruku, aby wyświetlić pasek przewijania, by mieć łatwy dostęp do dowolnej strony z dokumentu.  
  
-   Przyczyna podglądu wydruku, aby zachować pozycji użytkownika w dokumencie przez od jej wyświetlanie na bieżącej stronie.  
  
-   Powoduje wykonanie do drukowania i podglądu wydruku różnych inicjalizacji.  
  
-   Przyczyna podglądu wydruku, aby wyświetlić numery stron w własnych formatów.  
  
 Jeśli wiadomo, jak długo trwa dokumentu i wywołania `SetMaxPage` na odpowiednią wartość platformę można użyć tych informacji w wersji zapoznawczej, a także podczas drukowania. Gdy w ramach zna długość dokumentu, może udostępnić okna podglądu paska, dzięki czemu użytkownik i z powrotem stronę do dokumentu w wersji zapoznawczej przewijania. Nie zdefiniowano długość dokumentu, nie można określić położenia pole przewijania, aby wskazać bieżącą pozycję, dzięki czemu w ramach nie dodaje pasek przewijania przez platformę. W takim przypadku użytkownik musi użyć przyciski poprzedniej strony i następnej strony na pasek sterowania okna podglądu do strony do dokumentu.  
  
 Podglądu wydruku, może być przydatne do przypisania wartości do `m_nCurPage` członkiem `CPrintInfo`, mimo że może nigdy nie zrobisz zwykłej drukowania. Podczas drukowania zwykłej ten element członkowski przenosi informacje w ramach na klasę widoku. Jest to, jak platformę informuje widoku strony, która ma być drukowana.  
  
 Z kolei po uruchomieniu tryb podglądu wydruku, `m_nCurPage` elementu członkowskiego przenosi informacje, w przeciwnym kierunku: z widoku do struktury. Platformę używa wartość tego elementu członkowskiego w celu określenia, należy najpierw wyświetlić strony, która podglądu. Domyślna wartość tego elementu członkowskiego jest 1, co na pierwszej stronie dokumentu jest początkowo wyświetlane. Można zastąpić `OnPreparePrinting` można ustawić tego elementu członkowskiego do liczby wyświetlanej w czasie polecenie Podgląd wydruku został wywołany stronie. W ten sposób aplikacja przechowuje użytkownika bieżącego położenia przy przechodzeniu tryb wyświetlania normalnej do tryb podglądu wydruku.  
  
 Czasami może być `OnPreparePrinting` do wykonywania różnych inicjowania w zależności od tego, czy jest ona wywoływana dla zadania drukowania lub podglądu wydruku. Można to określić, sprawdzając **m_bPreview** zmiennej członkowskiej w `CPrintInfo` struktury. Ten element członkowski ma ustawioną wartość **TRUE** po wywołaniu podglądu wydruku.  
  
 `CPrintInfo` Struktura zawiera również element członkowski o nazwie **m_strPageDesc**, który jest używany do formatowania ciągi wyświetlane w dolnej części ekranu w trybach jednostronicowej i wielu stron. Domyślnie te ciągi są w formie "strony  *n* " i "stron  *n*   -  *m*,", ale można modyfikować **m_ strPageDesc** z poziomu `OnPreparePrinting` i ustaw ciągi na coś bardziej złożonych. Zobacz [cprintinfo — struktura](../mfc/reference/cprintinfo-structure.md) w *odwołania MFC* Aby uzyskać więcej informacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Drukowanie i Podgląd wydruku](../mfc/printing-and-print-preview.md)   
 [Drukowanie](../mfc/printing.md)   
 [Cview — klasa](../mfc/reference/cview-class.md)   
 [Klasa CDC](../mfc/reference/cdc-class.md)
