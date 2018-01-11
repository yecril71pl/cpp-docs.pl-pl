---
title: "Formanty MFC ActiveX: Dodawanie właściwości niestandardowych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], properties
- properties [MFC], custom
ms.assetid: 85af5167-74c7-427b-b8f3-e0d7b73942e5
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f64154142c4c5f0fb3f24dc63120799132983880
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-adding-custom-properties"></a>Kontrolki ActiveX MFC: dodawanie właściwości niestandardowych
Właściwości niestandardowe różnią się od właściwości podstawowe właściwości niestandardowe nie są już implementowana przez `COleControl` klasy. Właściwość niestandardowa służy do ujawniać niektórych stanu lub wygląd formantu ActiveX do programisty, za pomocą formantu.  
  
 W tym artykule opisano sposób dodawania właściwości niestandardowych do formantu ActiveX, za pomocą Kreatora dodawania właściwości i opisano wynikowy modyfikacji kodu. Tematy obejmują:  
  
-   [Dodawanie właściwości niestandardowych przy użyciu Kreatora dodawania właściwości](#_core_using_classwizard_to_add_a_custom_property)  
  
-   [Dodaj Kreatora właściwości zmiany właściwości niestandardowych](#_core_classwizard_changes_for_custom_properties)  
  
 Właściwości niestandardowe są dostępne w czterech odmian wykonania: zmienna elementu członkowskiego, powiadomienia, metod Get/Set i sparametryzowane zmiennej elementu członkowskiego.  
  
-   Implementacja zmiennej elementu członkowskiego  
  
     Ta implementacja reprezentuje stan właściwości jako zmienną członkowską do klasy formantu. Użyj zmiennej elementu członkowskiego implementacji, gdy nie jest ważne dowiedzieć się, gdy zmienia się wartość właściwości. Trzech typów ta implementacja tworzy minimalnej liczbie kod obsługi właściwości. Makro wpisu mapy wysyłania dla implementacji zmiennej elementu członkowskiego jest [disp_property —](../mfc/reference/dispatch-maps.md#disp_property).  
  
-   Zmiennej członkowskiej z implementacją powiadomień  
  
     Ta implementacja składa się z zmiennej członkowskiej i funkcję powiadomień utworzone przez Kreatora dodawania właściwości. Funkcja powiadomień automatycznie jest wywoływana przez platformę po zmianie wartości właściwości. Użyj zmiennej elementu członkowskiego z implementacją powiadomień gdy potrzebne są zgłaszane po zmianie wartości właściwości. Ta implementacja wymaga więcej czasu, ponieważ wymaga wywołania funkcji. Makro wpisu mapy wysyłania dla tej implementacji jest [disp_property_notify —](../mfc/reference/dispatch-maps.md#disp_property_notify).  
  
-   Implementacja metod Get/Set  
  
     Ta implementacja składa się z pary funkcji Członkowskich w klasy formantu. Implementacja metody Get i Set automatycznie wywołuje element członkowski Get funkcja bieżącą wartość właściwości żądanie formantu użytkownika i zestaw funkcji członkowskiej żądanie użytkownika formantu, można zmienić właściwości. Gdy do obliczenia wartości właściwości w czasie wykonywania sprawdzania poprawności wartości przekazywane przez kontrolki użytkownika przed zmianą właściwości rzeczywiste, lub implementować typ właściwości lub zapisu — tylko do odczytu, należy użyć tej implementacji. Makro wpisu mapy wysyłania dla tej implementacji jest [disp_property_ex —](../mfc/reference/dispatch-maps.md#disp_property_ex). Poniższej sekcji [Dodawanie właściwości niestandardowych przy użyciu Kreatora dodawania właściwości](#_core_using_classwizard_to_add_a_custom_property), używa właściwości niestandardowe CircleOffset aby zademonstrować tej implementacji.  
  
-   Implementacja sparametryzowane  
  
     Implementacja sparametryzowane jest obsługiwana przez Kreatora dodawania właściwości. Sparametryzowane właściwości (nazywane również tablicy właściwości) może służyć do zestawu wartości za pośrednictwem pojedynczej właściwości formantu. Makro wpisu mapy wysyłania dla tej implementacji jest `DISP_PROPERTY_PARAM`. Aby uzyskać więcej informacji na ten typ implementacji, zobacz [implementacja właściwości sparametryzowana](../mfc/mfc-activex-controls-advanced-topics.md) w artykule formantów ActiveX: Tematy zaawansowane.  
  
##  <a name="_core_using_classwizard_to_add_a_custom_property"></a>Przy użyciu Dodaj Kreatora właściwości, aby dodać właściwości niestandardowe  
 W poniższej procedurze przedstawiono dodawanie właściwości niestandardowych CircleOffset, używanym w implementacji metody Get i Set. Właściwość niestandardowa CircleOffset umożliwia użytkownikowi formantu przesunięcie koło z Centrum prostokątem formantu. Dodawanie właściwości niestandardowych z implementacją innego niż metod Get/Set procedura jest bardzo podobne.  
  
 Tę samą procedurę można również inne właściwości niestandardowe, które chcesz dodać. Zastąp nazwę właściwości niestandardowej nazwy właściwości CircleOffset i parametrów.  
  
#### <a name="to-add-the-circleoffset-custom-property-using-the-add-property-wizard"></a>Aby dodać właściwości niestandardowe CircleOffset za pomocą Kreatora dodawania właściwości  
  
1.  Załaduj projekt z kontroli.  
  
2.  W widoku klas rozwiń węzeł Biblioteka formantu.  
  
3.  Kliknij prawym przyciskiem myszy węzeł interfejsu dla formantu (drugiego węzła węzeł biblioteki), aby otworzyć menu skrótów.  
  
4.  W menu skrótów kliknij **Dodaj** , a następnie kliknij przycisk **Dodaj właściwość**.  
  
     Spowoduje to otwarcie [Dodaj Kreatora właściwości](../ide/names-add-property-wizard.md).  
  
5.  W **nazwa właściwości** wpisz `CircleOffset`.  
  
6.  Aby uzyskać **typ implementacji**, kliknij przycisk **metod Get/Set**.  
  
7.  W **typ właściwości** wybierz opcję **krótki**.  
  
8.  Wpisz unikatowe nazwy Get i ustawić funkcji lub zaakceptuj domyślne nazwy.  
  
9. Kliknij przycisk **Zakończ**.  
  
##  <a name="_core_classwizard_changes_for_custom_properties"></a>Dodaj Kreatora właściwości zostanie zmieniona dla właściwości niestandardowe  
 Po dodaniu niestandardowej właściwości CircleOffset Kreatora dodawania właściwości wprowadza zmiany do nagłówka (. H), jak i implementację (. Pliki CPP) klasy formantu.  
  
 Następujące wiersze są dodawane do. Plik H, aby zadeklarować dwóch funkcji o nazwie `GetCircleOffset` i `SetCircleOffset`:  
  
 [!code-cpp[NVC_MFC_AxUI#25](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_1.h)]  
  
 Następujący wiersz jest dodawany do formantu. Plik IDL:  
  
 [!code-cpp[NVC_MFC_AxUI#26](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_2.idl)]  
  
 Ten wiersz przypisuje właściwości CircleOffset na określony numer ID pobierane z metody pozycję na liście właściwości i metody w Kreatorze dodawania właściwości.  
  
 Ponadto następujące wiersz zostanie dodany do mapy wysyłania (w. Pliku CPP klasy formantu) do mapowania właściwości CircleOffset formantu dwie funkcje programu obsługi:  
  
 [!code-cpp[NVC_MFC_AxUI#27](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_3.cpp)]  
  
 Na koniec implementacje `GetCircleOffset` i `SetCircleOffset` funkcje są dodawane na końcu formantu. Pliku CPP. W większości przypadków należy zmodyfikować funkcji Get zwraca wartość właściwości. Funkcja zestawu zazwyczaj zawiera kod, który ma być wykonany przed lub po zmianie właściwości.  
  
 [!code-cpp[NVC_MFC_AxUI#28](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_4.cpp)]  
  
 Należy pamiętać, że Kreator dodawania właściwości automatycznie dodaje wywołanie, do [SetModifiedFlag](../mfc/reference/colecontrol-class.md#setmodifiedflag), aby treści funkcji zestawu. Wywołanie tej funkcji oznacza formant jako zmodyfikowane. Jeśli formant został zmodyfikowany, jego nowego stanu zostaną zapisane przy zapisywaniu kontenera. Ta funkcja powinna być wywoływana zmianie wartości właściwości zapisywane jako część trwały stan formantu.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Formanty MFC ActiveX: właściwości](../mfc/mfc-activex-controls-properties.md)   
 [Formanty MFC ActiveX: metody](../mfc/mfc-activex-controls-methods.md)   
 [Klasa COleControl](../mfc/reference/colecontrol-class.md)
