---
title: 'Kontrolki ActiveX MFC: Dodawanie właściwości niestandardowych'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], properties
- properties [MFC], custom
ms.assetid: 85af5167-74c7-427b-b8f3-e0d7b73942e5
ms.openlocfilehash: e02d5523b894f89aa93c8d2765a128920afa2353
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392781"
---
# <a name="mfc-activex-controls-adding-custom-properties"></a>Kontrolki ActiveX MFC: Dodawanie właściwości niestandardowych

Właściwości niestandardowe różnią się od właściwości podstawowe, w tym, że właściwości niestandardowe nie są już zaimplementowany przez `COleControl` klasy. Właściwość niestandardowa jest używana do udostępnienia określonego stanu lub wyglądu formantu ActiveX do programisty, za pomocą formantu.

W tym artykule opisano, jak dodać właściwość niestandardową do formantu ActiveX, za pomocą Kreatora dodawania właściwości i wyjaśnia wynikowy modyfikacji kodu. Tematy obejmują:

- [Dodawanie właściwości niestandardowych przy użyciu Kreatora dodawania właściwości](#_core_using_classwizard_to_add_a_custom_property)

- [Dodaj Kreatora właściwości zmiany właściwości niestandardowych](#_core_classwizard_changes_for_custom_properties)

Właściwości niestandardowe są dostępne w cztery różne typy wdrożenia: Zmiennej składowej, zmiennej składowej, z powiadomieniem, metod Get/Set i sparametryzowanych.

- Implementacja zmiennej elementu członkowskiego

   Ta implementacja reprezentuje stan właściwości jako zmienną elementu członkowskiego w klasie kontrolki. Jeśli nie jest to ważne, aby wiedzieć, kiedy ulega zmianie wartość właściwości, należy użyć zmiennej elementu członkowskiego implementacji. Z trzech typów ta implementacja tworzy najmniejszą ilością kod pomocy technicznej dla właściwości. Makro wpis mapy wysyłania dla implementacji zmiennej elementu członkowskiego jest [DISP_PROPERTY](../mfc/reference/dispatch-maps.md#disp_property).

- Zmiennej składowej z implementacją powiadomień

   Ta implementacja składa się z zmienną członkowską i funkcję powiadomień, utworzony za pomocą Dodaj Kreatora właściwości. Funkcja powiadomień automatycznie jest wywoływane przez platformę po zmianie wartości właściwości. Użyj zmiennej elementu członkowskiego z implementacją powiadomień gdy potrzebujesz otrzymać powiadomienie po zmianie wartości właściwości. Ta implementacja wymaga więcej czasu, ponieważ wymaga wywołania funkcji. Makro wpis mapy wysyłania dla tej implementacji [DISP_PROPERTY_NOTIFY](../mfc/reference/dispatch-maps.md#disp_property_notify).

- Implementacja metody GET/Set

   Ta implementacja składa się z dwóch funkcji składowych w klasie kontrolki. Implementacja metody Get/Set automatycznie wywołuje członka Get funkcja bieżąca wartość właściwości żądanie formantu użytkownika i funkcja elementu członkowskiego zestawu po użytkownik formantu zażąda, można zmienić właściwości. Użyj tej implementacji, gdy to konieczne do obliczenia wartości właściwości w czasie wykonywania, sprawdzania poprawności wartości przekazane przez użytkownika kontrolki przed zmianą właściwości rzeczywiste, oraz implementowanie typu właściwości lub zapisu — tylko do odczytu. Makro wpis mapy wysyłania dla tej implementacji [DISP_PROPERTY_EX](../mfc/reference/dispatch-maps.md#disp_property_ex). Poniższej sekcji [Dodawanie właściwości niestandardowych przy użyciu Kreatora dodawania właściwości](#_core_using_classwizard_to_add_a_custom_property), używa niestandardowej właściwości CircleOffset aby zademonstrować tę implementację.

- Implementacja sparametryzowane

   Implementacja sparametryzowane jest obsługiwana przez Kreatora dodawania właściwości. Właściwości sparametryzowane (czasami nazywany tablicy właściwości) może służyć dostęp do zestawu wartości za pośrednictwem pojedynczej właściwości formantu. Makra wpis mapy wysyłania dla tej implementacji jest DISP_PROPERTY_PARAM. Aby uzyskać więcej informacji dotyczących implementowania tego typu, zobacz [Implementowanie właściwości sparametryzowane](../mfc/mfc-activex-controls-advanced-topics.md) w artykule kontrolek ActiveX: Tematy zaawansowane.

##  <a name="_core_using_classwizard_to_add_a_custom_property"></a> Za pomocą Dodaj Kreatora właściwości, aby dodać właściwość niestandardową

Poniższa procedura demonstruje, dodawanie właściwości niestandardowych CircleOffset, który używa implementacji metod Get/Set. Niestandardowa właściwość CircleOffset umożliwia użytkownikowi formantu przesunięcie koło z Centrum prostokąt otaczający formantu. Procedura dodawania właściwości niestandardowych z implementacją innego niż metod Get/Set jest bardzo podobne.

Tę samą procedurę można również inne właściwości niestandardowe, które chcesz dodać. Zastąp nazwę właściwości niestandardowej CircleOffset nazwy właściwości i parametrów.

#### <a name="to-add-the-circleoffset-custom-property-using-the-add-property-wizard"></a>Aby dodać właściwości niestandardowe CircleOffset za pomocą Kreatora dodawania właściwości

1. Załaduj projekt formantu.

1. W widoku klas rozwiń węzeł biblioteki kontrolki.

1. Kliknij prawym przyciskiem myszy węzeł interfejsu dla kontrolki (drugi węzeł węzła biblioteki), aby otworzyć menu skrótów.

1. W menu skrótów kliknij **Dodaj** a następnie kliknij przycisk **Dodaj właściwość**.

   Spowoduje to otwarcie [Kreator dodawania właściwości](../ide/names-add-property-wizard.md).

1. W **nazwa właściwości** wpisz *CircleOffset*.

1. Aby uzyskać **typ implementacji**, kliknij przycisk **metod Get/Set**.

1. W **typ właściwości** wybierz opcję **krótki**.

1. Wpisz unikatowe nazwy, Pobierz i ustaw funkcji, lub zaakceptować domyślne nazwy.

9. Kliknij przycisk **Zakończ**.

##  <a name="_core_classwizard_changes_for_custom_properties"></a> Dodaj zmiany Kreatora właściwości dla właściwości niestandardowe

Podczas dodawania właściwości niestandardowych CircleOffset Kreator dodawania właściwości sprawia, że zmiany do nagłówka (. Godz.), jak i implementację (. Plikach CPP) klasy kontrolki.

Następujące wiersze są dodawane do. Plik H, aby zadeklarować dwie funkcje o nazwie `GetCircleOffset` i `SetCircleOffset`:

[!code-cpp[NVC_MFC_AxUI#25](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_1.h)]

Następujący wiersz jest dodawany do formantu. Plik IDL:

[!code-cpp[NVC_MFC_AxUI#26](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_2.idl)]

Ten wiersz przypisuje właściwość CircleOffset określonych numer identyfikacyjny pobranych z metody pozycji na liście właściwości i metod w Kreatorze dodawania właściwości.

Ponadto dodaje się następujący wiersz do mapy wysyłania (w. Plik CPP klasy kontrolki) do mapowania właściwości CircleOffset dwie funkcje obsługi formantu:

[!code-cpp[NVC_MFC_AxUI#27](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_3.cpp)]

Na koniec implementacje `GetCircleOffset` i `SetCircleOffset` funkcje są dodawane na końcu formantu. Plik CPP. W większości przypadków należy zmodyfikować funkcję Get w celu zwrócenia wartości właściwości. Funkcja Set zazwyczaj zawiera kod, który ma być wykonany przed lub po zmianie właściwości.

[!code-cpp[NVC_MFC_AxUI#28](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_4.cpp)]

Należy pamiętać, że Kreator dodawania właściwości automatycznie dodaje połączenie, do [SetModifiedFlag](../mfc/reference/colecontrol-class.md#setmodifiedflag), do treści funkcji Set. Wywołanie tej funkcji oznacza kontrolkę, jak modyfikacji. W przypadku modyfikowania kontrolki jego nowego stanu zostaną zapisane przy zapisywaniu kontenera. Ta funkcja powinna być wywoływana zawsze wtedy, gdy właściwość zapisane jako części kontrolki trwały stan zmieni się wartość.

## <a name="see-also"></a>Zobacz także

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Kontrolki ActiveX MFC: właściwości](../mfc/mfc-activex-controls-properties.md)<br/>
[Kontrolki ActiveX MFC: metody](../mfc/mfc-activex-controls-methods.md)<br/>
[Klasa COleControl](../mfc/reference/colecontrol-class.md)
