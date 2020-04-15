---
title: 'Kontrolki ActiveX MFC: dodawanie właściwości niestandardowych'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], properties
- properties [MFC], custom
ms.assetid: 85af5167-74c7-427b-b8f3-e0d7b73942e5
ms.openlocfilehash: 00f7a879582bca562ce626fe224206094fd19bc7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364703"
---
# <a name="mfc-activex-controls-adding-custom-properties"></a>Kontrolki ActiveX MFC: dodawanie właściwości niestandardowych

Właściwości niestandardowe różnią się od właściwości magazynowych, ponieważ właściwości `COleControl` niestandardowe nie są już implementowane przez klasę. Właściwość niestandardowa jest używana do uwidaczniania określonego stanu lub wyglądu formantu ActiveX dla programisty używającego formantu.

W tym artykule opisano sposób dodawania właściwości niestandardowej do formantu ActiveX za pomocą Kreatora dodawania właściwości i wyjaśniono wynikające z tego modyfikacje kodu. Tematy obejmują:

- [Dodawanie właściwości za pomocą Kreatora dodawania właściwości](#_core_using_classwizard_to_add_a_custom_property)

- [Dodawanie zmian Kreatora właściwości dla właściwości niestandardowych](#_core_classwizard_changes_for_custom_properties)

Właściwości niestandardowe są dostępne w czterech odmianach implementacji: Zmienna elementu członkowskiego, Zmienna elementu członkowskiego z powiadomieniem, Metody pobierz/zestaw i Parametryzowane.

- Implementacja zmiennej elementu członkowskiego

   Ta implementacja reprezentuje stan właściwości jako zmienną elementu członkowskiego w klasie kontroli. Użyj implementacji zmiennej elementu członkowskiego, gdy nie jest ważne, aby wiedzieć, kiedy zmienia się wartość właściwości. Z trzech typów ta implementacja tworzy najmniejszą ilość kodu pomocy technicznej dla właściwości. Makro wpisu mapy wysyłki dla implementacji zmiennej członkowskiej jest [DISP_PROPERTY](../mfc/reference/dispatch-maps.md#disp_property).

- Zmienna elementu członkowskiego z implementacją powiadomień

   Ta implementacja składa się ze zmiennej członkowskiej i funkcji powiadomień utworzonej przez Kreatora dodawania właściwości. Funkcja powiadomień jest automatycznie wywoływana przez platformę po zmianie wartości właściwości. Użyj zmiennej elementu członkowskiego z implementacją notification, gdy musisz otrzymywać powiadomienia po zmianie wartości właściwości. Ta implementacja wymaga więcej czasu, ponieważ wymaga wywołania funkcji. Makro wpisu mapy wysyłki dla tej implementacji jest [DISP_PROPERTY_NOTIFY](../mfc/reference/dispatch-maps.md#disp_property_notify).

- Implementacja metod get/set

   Ta implementacja składa się z pary funkcji członkowskich w klasie kontroli. Implementacja Metody Get/Set automatycznie wywołuje funkcję Get member, gdy użytkownik formantu żąda bieżącej wartości właściwości i funkcji Set member, gdy użytkownik formantu zażąda zmiany właściwości. Tej implementacji należy użyć, gdy trzeba obliczyć wartość właściwości w czasie wykonywania, sprawdź poprawność wartości przekazanej przez użytkownika formantu przed zmianą właściwości rzeczywistej lub zaimplementować typ właściwości tylko do odczytu lub zapisu. Makro wpisu mapy wysyłki dla tej implementacji jest [DISP_PROPERTY_EX](../mfc/reference/dispatch-maps.md#disp_property_ex). W poniższej sekcji [za pomocą Kreatora dodawania właściwości do dodawania właściwości niestandardowej](#_core_using_classwizard_to_add_a_custom_property)używa właściwości niestandardowej CircleOffset, aby zademonstrować tę implementację.

- Implementacja sparametryzowana

   Implementacja parametryzowana jest obsługiwana przez Kreatora dodawania właściwości. Właściwość sparametryzowana (czasami nazywana tablicą właściwości) może służyć do uzyskiwania dostępu do zestawu wartości za pośrednictwem jednej właściwości formantu. Makro wpisu mapy wysyłki dla tej implementacji jest DISP_PROPERTY_PARAM. Aby uzyskać więcej informacji na temat implementowania tego typu, zobacz [Implementowanie właściwości sparametryzowanej](../mfc/mfc-activex-controls-advanced-topics.md) w artykule ActiveX Controls: Advanced Topics.

## <a name="using-the-add-property-wizard-to-add-a-custom-property"></a><a name="_core_using_classwizard_to_add_a_custom_property"></a>Dodawanie właściwości niestandardowej za pomocą Kreatora dodawania właściwości

Poniższa procedura pokazuje dodanie właściwości niestandardowej CircleOffset, która używa implementacji Metody Get/Set. Właściwość niestandardowa CircleOffset umożliwia użytkownikowi formantu przesunięcie okręgu od środka prostokąta ograniczającego formantu. Procedura dodawania właściwości niestandardowych z implementacją inną niż Metody Get/Set jest bardzo podobna.

Ta sama procedura może również służyć do dodawania innych właściwości niestandardowych, które chcesz. Zastąp nazwę właściwości niestandardowej nazwą i parametrami właściwości CircleOffset.

#### <a name="to-add-the-circleoffset-custom-property-using-the-add-property-wizard"></a>Aby dodać właściwość niestandardową CircleOffset za pomocą Kreatora dodawania właściwości

1. Załaduj projekt formantu.

1. W widoku klasy rozwiń węzeł biblioteki formantu.

1. Kliknij prawym przyciskiem myszy węzeł interfejsu formantu (drugi węzeł węzła biblioteki), aby otworzyć menu skrótów.

1. W menu skrótów kliknij polecenie **Dodaj,** a następnie kliknij pozycję **Dodaj właściwość**.

   Spowoduje to otwarcie [Kreatora dodawania właściwości](../ide/names-add-property-wizard.md).

1. W polu **Nazwa właściwości** wpisz *CircleOffset*.

1. W przypadku **typu implementacji**kliknij pozycję **Pobierz/Ustaw metody**.

1. W polu **Typ właściwości** wybierz **krótki**.

1. Wpisz unikatowe nazwy funkcji Pobierz i Ustaw lub zaakceptuj nazwy domyślne.

1. Kliknij przycisk **Zakończ**.

## <a name="add-property-wizard-changes-for-custom-properties"></a><a name="_core_classwizard_changes_for_custom_properties"></a>Dodawanie zmian kreatora właściwości dla właściwości niestandardowych

Po dodaniu właściwości niestandardowej CircleOffset Kreator dodawania właściwości wprowadza zmiany w nagłówku (. H) i wdrożenie (. CPP) w klasie kontrolnej.

Następujące wiersze są dodawane do . H plik do deklarowania dwóch funkcji o nazwie `GetCircleOffset` i: `SetCircleOffset`

[!code-cpp[NVC_MFC_AxUI#25](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_1.h)]

Następujący wiersz jest dodawany do formantu . Plik IDL:

[!code-cpp[NVC_MFC_AxUI#26](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_2.idl)]

Ten wiersz przypisuje CircleOffset właściwość określony numer identyfikatora, zaczerpnięte z pozycji metody na liście metod i właściwości Kreatora dodawania właściwości.

Ponadto do mapy wysyłki dodaje się następujący wiersz (w pliku . CPP klasy formantu), aby zamapować Właściwość CircleOffset na dwie funkcje obsługi formantu:

[!code-cpp[NVC_MFC_AxUI#27](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_3.cpp)]

Na koniec implementacje `GetCircleOffset` funkcji `SetCircleOffset` i są dodawane na końcu kontroli . CPP. W większości przypadków zmodyfikujesz Get funkcji, aby zwrócić wartość właściwości. Funkcja Set zwykle zawiera kod, który powinien zostać wykonany przed lub po zmianie właściwości.

[!code-cpp[NVC_MFC_AxUI#28](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_4.cpp)]

Należy zauważyć, że Kreator dodawania właściwości automatycznie dodaje wywołanie do [SetModifiedFlag](../mfc/reference/colecontrol-class.md#setmodifiedflag)do treści funkcji Ustaw. Wywołanie tej funkcji oznacza formant jako zmodyfikowany. Jeśli formant został zmodyfikowany, jego nowy stan zostanie zapisany po zapisaniu kontenera. Ta funkcja powinna być wywoływana za każdym razem, gdy właściwość, zapisane jako część stanu trwałego formantu, zmienia wartość.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Kontrolki ActiveX MFC: właściwości](../mfc/mfc-activex-controls-properties.md)<br/>
[Kontrolki ActiveX MFC: metody](../mfc/mfc-activex-controls-methods.md)<br/>
[Klasa COleControl](../mfc/reference/colecontrol-class.md)
