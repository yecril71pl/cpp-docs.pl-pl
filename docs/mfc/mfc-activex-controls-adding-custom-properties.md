---
title: 'Kontrolki ActiveX MFC: dodawanie właściwości niestandardowych'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], properties
- properties [MFC], custom
ms.assetid: 85af5167-74c7-427b-b8f3-e0d7b73942e5
ms.openlocfilehash: af1ca2d63abcb112bfe1e7d7538dbf70fb817ae5
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503886"
---
# <a name="mfc-activex-controls-adding-custom-properties"></a>Kontrolki ActiveX MFC: dodawanie właściwości niestandardowych

Właściwości niestandardowe różnią się od właściwości podstawowych w tym, że właściwości niestandardowe nie zostały już zaimplementowane przez `COleControl` klasę. Właściwość niestandardowa służy do ujawnienia pewnego stanu lub wyglądu kontrolki ActiveX programisty przy użyciu formantu.

W tym artykule opisano sposób dodawania niestandardowej właściwości do kontrolki ActiveX przy użyciu Kreatora dodawania właściwości i objaśniające modyfikacje kodu. Tematy obejmują:

- [Za pomocą Kreatora dodawania właściwości, aby dodać właściwość niestandardową](#_core_using_classwizard_to_add_a_custom_property)

- [Dodawanie zmian kreatora właściwości dla właściwości niestandardowych](#_core_classwizard_changes_for_custom_properties)

Właściwości niestandardowe są dostępne w czterech odmianach implementacji: zmienna członkowska, zmienna członkowska z powiadomieniami, metoda get/set i sparametryzowane.

- Implementacja zmiennej składowej

   Ta implementacja reprezentuje stan właściwości jako zmienną członkowską w klasie Control. Użyj implementacji zmiennej składowej, gdy nie jest ważne, aby wiedzieć, kiedy zmienia się wartość właściwości. Z trzech typów Ta implementacja powoduje utworzenie najmniejszej ilości kodu pomocy technicznej dla właściwości. Makro wpisu mapy wysyłania dla implementacji zmiennej składowej jest [DISP_PROPERTY](reference/dispatch-maps.md#disp_property).

- Zmienna członkowska z implementacją powiadomień

   Ta implementacja zawiera zmienną członkowską i funkcję powiadamiania utworzoną przez Kreatora dodawania właściwości. Funkcja powiadomień jest automatycznie wywoływana przez platformę po zmianie wartości właściwości. Użyj zmiennej składowej z implementacją powiadomień, gdy musisz otrzymywać powiadomienia po zmianie wartości właściwości. Ta implementacja wymaga więcej czasu, ponieważ wymaga wywołania funkcji. Makro wpisu mapy wysyłania dla tej implementacji ma [DISP_PROPERTY_NOTIFY](reference/dispatch-maps.md#disp_property_notify).

- Implementacja metod get/set

   Ta implementacja składa się z pary funkcji Członkowskich w klasie Control. Implementacja metod get/set automatycznie wywołuje funkcję Get member, gdy użytkownik kontrolki żąda bieżącej wartości właściwości i funkcji zestawu, gdy użytkownik kontrolki żąda zmiany właściwości. Użyj tej implementacji, gdy musisz obliczyć wartość właściwości w czasie wykonywania, sprawdzić poprawność wartości przesłanej przez użytkownika kontrolki przed zmianą rzeczywistej właściwości lub zaimplementować typ właściwości tylko do odczytu lub zapisu. Makro wpisu mapy wysyłania dla tej implementacji ma [DISP_PROPERTY_EX](reference/dispatch-maps.md#disp_property_ex). W poniższej sekcji [za pomocą Kreatora dodawania właściwości, aby dodać właściwość niestandardową](#_core_using_classwizard_to_add_a_custom_property), program używa właściwości niestandardowej CircleOffset w celu zademonstrowania tej implementacji.

- Implementacja sparametryzowane

   Implementacja sparametryzowanej jest obsługiwana przez Kreatora dodawania właściwości. Właściwość sparametryzowane (czasami nazywana tablicą właściwości) może być używana do uzyskiwania dostępu do zestawu wartości za pomocą pojedynczej właściwości kontrolki. Makro wpisu mapy wysyłania dla tej implementacji ma DISP_PROPERTY_PARAM. Aby uzyskać więcej informacji na temat implementowania tego typu, zobacz [implementowanie właściwości sparametryzowanej](mfc-activex-controls-advanced-topics.md) w formantach ActiveX artykułów: Tematy zaawansowane.

## <a name="using-the-add-property-wizard-to-add-a-custom-property"></a><a name="_core_using_classwizard_to_add_a_custom_property"></a> Za pomocą Kreatora dodawania właściwości, aby dodać właściwość niestandardową

Poniższa procedura przedstawia Dodawanie właściwości niestandardowej CircleOffset, która używa implementacji metod get/set. Właściwość niestandardowa CircleOffset umożliwia użytkownikowi kontrolce przesunięcie okręgu od środka prostokąta obwiedni kontrolki. Procedura dodawania właściwości niestandardowych z implementacją inną niż metody get/set jest bardzo podobna.

Tę samą procedurę można także użyć w celu dodania innych niestandardowych właściwości. Zastąp niestandardową nazwę właściwości dla nazwy i parametrów właściwości CircleOffset.

#### <a name="to-add-the-circleoffset-custom-property-using-the-add-property-wizard"></a>Aby dodać właściwość niestandardową CircleOffset za pomocą Kreatora dodawania właściwości

1. Załaduj projekt kontrolki.

1. W Widok klasy rozwiń węzeł Biblioteka formantu.

1. Kliknij prawym przyciskiem myszy węzeł interfejsu dla formantu (drugi węzeł węzła biblioteki), aby otworzyć menu skrótów.

1. W menu skrótów kliknij polecenie **Dodaj** , a następnie kliknij przycisk **Dodaj właściwość**.

   Spowoduje to otwarcie [Kreatora dodawania właściwości](../ide/adding-a-property-visual-cpp.md#names-add-property-wizard).

1. W polu **Nazwa właściwości** wpisz *CircleOffset*.

1. W obszarze **Typ implementacji**kliknij pozycję **Pobierz/ustaw metody**.

1. W polu **Typ właściwości** wybierz opcję **`short`** .

1. Wpisz unikatowe nazwy dla funkcji get i set lub zaakceptuj nazwy domyślne.

1. Kliknij przycisk **Zakończ**.

## <a name="add-property-wizard-changes-for-custom-properties"></a><a name="_core_classwizard_changes_for_custom_properties"></a> Dodawanie zmian kreatora właściwości dla właściwości niestandardowych

Po dodaniu właściwości niestandardowej CircleOffset Kreator dodawania właściwości wprowadza zmiany do nagłówka (. H) i implementację (. CPP) pliki klasy Control.

Do programu są dodawane następujące wiersze. H plik do deklarowania dwóch funkcji o nazwie `GetCircleOffset` i `SetCircleOffset` :

[!code-cpp[NVC_MFC_AxUI#25](codesnippet/cpp/mfc-activex-controls-adding-custom-properties_1.h)]

Do kontrolki zostanie dodany następujący wiersz. Plik IDL:

[!code-cpp[NVC_MFC_AxUI#26](codesnippet/cpp/mfc-activex-controls-adding-custom-properties_2.idl)]

Ten wiersz przypisuje Właściwość CircleOffset określony numer IDENTYFIKACYJNy, pobrany z pozycji metody z listy metody i właściwości Kreatora dodawania właściwości.

Ponadto Poniższy wiersz jest dodawany do mapy wysyłania (w. CPP plik klasy kontrolki, aby zamapować właściwość CircleOffset na dwie funkcje obsługi formantu:

[!code-cpp[NVC_MFC_AxUI#27](codesnippet/cpp/mfc-activex-controls-adding-custom-properties_3.cpp)]

Wreszcie implementacje `GetCircleOffset` `SetCircleOffset` funkcji i są dodawane na końcu kontrolki. Plik CPP. W większości przypadków zmodyfikujesz funkcję Get, aby zwracała wartość właściwości. Funkcja Set zwykle zawiera kod, który powinien być wykonany przed lub po zmianie właściwości.

[!code-cpp[NVC_MFC_AxUI#28](codesnippet/cpp/mfc-activex-controls-adding-custom-properties_4.cpp)]

Należy zauważyć, że Kreator dodawania właściwości automatycznie dodaje wywołanie do [SetModifiedFlag](reference/colecontrol-class.md#setmodifiedflag)do treści funkcji Set. Wywołanie tej funkcji oznacza kontrolkę jako zmodyfikowaną. Jeśli formant został zmodyfikowany, jego nowy stan zostanie zapisany podczas zapisywania kontenera. Ta funkcja powinna być wywoływana zawsze, gdy właściwość jest zapisywana jako część trwałego stanu kontrolki, zmienia wartość.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](mfc-activex-controls.md)<br/>
[Kontrolki ActiveX MFC: właściwości](mfc-activex-controls-properties.md)<br/>
[Kontrolki ActiveX MFC: metody](mfc-activex-controls-methods.md)<br/>
[Klasa COleControl](reference/colecontrol-class.md)
