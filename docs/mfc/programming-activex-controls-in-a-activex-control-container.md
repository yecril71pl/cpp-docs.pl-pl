---
title: 'Kontenery formantów ActiveX: programowanie formantów ActiveX w kontenerze formantów ActiveX'
ms.date: 09/12/2018
helpviewer_keywords:
- ActiveX control containers [MFC], accessing ActiveX controls
- Confirm Classes dialog box
- wrapper classes [MFC], ActiveX controls
- ActiveX control containers [MFC], wrapper classes
- ActiveX controls [MFC], accessing
- MFC ActiveX controls [MFC], accessing in containers
- header files [MFC], for ActiveX control wrapper class
- wrapper classes [MFC], using
- ActiveX controls [MFC], wrapper classes
ms.assetid: ef9b2480-92d6-4191-b16e-8055c4fd7b73
ms.openlocfilehash: 9620f4d47197147db4972c9f2024f6018a705902
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371185"
---
# <a name="activex-control-containers-programming-activex-controls-in-an-activex-control-container"></a>Kontenery formantów ActiveX: programowanie formantów ActiveX w kontenerze formantów ActiveX

W tym artykule opisano proces uzyskiwania dostępu do [metod](../mfc/mfc-activex-controls-methods.md) i właściwości narażonych [formantów](../mfc/mfc-activex-controls-properties.md) ActiveX.

>[!IMPORTANT]
> ActiveX to starsza technologia, która nie powinna być używana do nowego rozwoju. Aby uzyskać więcej informacji na temat nowoczesnych technologii, które zastępują ActiveX, zobacz [ActiveX Controls](activex-controls.md).

Zasadniczo, należy wykonać następujące kroki:

1. [Wstaw formant ActiveX do projektu kontenera ActiveX](../mfc/inserting-a-control-into-a-control-container-application.md) przy użyciu galerii.

1. [Zdefiniuj zmienną elementu członkowskiego](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md) (lub inną formę dostępu) tego samego typu co klasa otoki kontrolnej ActiveX.

1. [Program ActiveX kontroli](#_core_programming_the_activex_control) przy użyciu wstępnie zdefiniowanych funkcji członkowskich klasy otoki.

W tej dyskusji załóżmy, że utworzono projekt oparty na oknie dialogowym (o nazwie Kontener) z obsługą kontroli ActiveX. Kontrola próbki Circ, Circ, zostanie dodana do wynikowego projektu.

Po wstawieniu circ formant do projektu (krok 1), wstawić wystąpienie Circ kontroli do głównego okna dialogowego aplikacji.

## <a name="procedures"></a>Procedury

#### <a name="to-add-the-circ-control-to-the-dialog-template"></a>Aby dodać kontrolka Circ do szablonu okna dialogowego

1. Załaduj projekt kontenera sterowania ActiveX. W tym przykładzie `Container` użyj projektu.

1. Kliknij kartę Widok zasobów.

1. Otwórz folder **Okno dialogowe.**

1. Kliknij dwukrotnie szablon głównego okna dialogowego. W tym przykładzie użyj **IDD_CONTAINER_DIALOG**.

1. Kliknij ikonę kontrolki Circ w przyborniku.

1. Kliknij punkt w oknie dialogowym, aby wstawić kontrolkę Circ.

1. Z menu **Plik** wybierz polecenie **Zapisz wszystko,** aby zapisać wszystkie modyfikacje w szablonie okna dialogowego.

## <a name="modifications-to-the-project"></a>Modyfikacje projektu

Aby umożliwić aplikacji Container dostęp do kontroli Circ, Visual C++`CCirc`automatycznie dodaje plik implementacji klasy otoki ( ) (. CPP) do projektu Container i nagłówka klasy otoki (. H) plik do pliku nagłówka okna dialogowego:

[!code-cpp[NVC_MFC_AxCont#1](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_1.h)]

## <a name="the-wrapper-class-header-h-file"></a><a name="_core_the_wrapper_class_header_28h29_file"></a>Nagłówek klasy otoki (. H) Plik

Aby uzyskać i ustawić właściwości (i wywołać metody) `CCirc` dla Circ kontroli, klasa otoki zawiera deklarację wszystkich metod i właściwości narażonych. W tym przykładzie te deklaracje znajdują się w CIRC. H. Poniższa próbka jest `CCirc` częścią klasy, która definiuje odsłonięte interfejsy formantu ActiveX:

[!code-cpp[NVC_MFC_AxCont#2](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_2.h)]
[!code-cpp[NVC_MFC_AxCont#3](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_3.h)]

Te funkcje mogą być następnie wywoływane z innych procedur aplikacji przy użyciu normalnej składni C++. Aby uzyskać więcej informacji na temat korzystania z tej funkcji elementu członkowskiego zestaw dostępu do metod i właściwości formantu, zobacz sekcję [Programowanie ActiveX kontroli](#_core_programming_the_activex_control).

## <a name="member-variable-modifications-to-the-project"></a><a name="_core_member_variable_modifications_to_the_project"></a>Modyfikacje zmiennej elementu członkowskiego w projekcie

Po activex formant został dodany do projektu i osadzone w kontenerze okna dialogowego, może być dostępny przez inne części projektu. Najprostszym sposobem uzyskania dostępu do formantu jest utworzenie `CContainerDlg` [zmiennej członkowskiej](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md) klasy okna dialogowego (krok 2), która jest tego samego typu co klasa otoki dodana do projektu przez visual C++. Następnie można użyć zmiennej elementu członkowskiego, aby uzyskać dostęp do osadzonego formantu w dowolnym momencie.

Gdy okno dialogowe **Dodawanie zmiennej elementu członkowskiego** dodaje do projektu zmienną *m_circctl,* dodaje również następujące wiersze do pliku nagłówka (. H) `CContainerDlg` klasy:

[!code-cpp[NVC_MFC_AxCont#4](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_4.h)]
[!code-cpp[NVC_MFC_AxCont#5](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_5.h)]

Ponadto, wezwanie do **DDX_Control** jest automatycznie dodawane `CContainerDlg`do "s `DoDataExchange`realizacji:

[!code-cpp[NVC_MFC_AxCont#6](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_6.cpp)]

## <a name="programming-the-activex-control"></a><a name="_core_programming_the_activex_control"></a>Programowanie formantu ActiveX

W tym momencie wstawiono formant ActiveX do szablonu okna dialogowego i utworzono dla niego zmienną elementu członkowskiego. Teraz można użyć wspólnej składni Języka C++, aby uzyskać dostęp do właściwości i metod formantu osadzonego.

Jak wspomniano (w [nagłówku klasy otoki (. H) Plik](#_core_the_wrapper_class_header_28h29_file)), plik nagłówka (. H) dla `CCirc` klasy otoki, w tym przypadku CIRC. H, zawiera listę funkcji członkowskich, których można użyć, aby uzyskać i ustawić dowolną wartość właściwości narażonych. Dostępne są również funkcje elementów członkowskich dla metod narażonych.

Wspólne miejsce do modyfikowania właściwości formantu `OnInitDialog` jest w funkcji elementu członkowskiego głównej klasy okna dialogowego. Ta funkcja jest wywoływana tuż przed wyświetleniem okna dialogowego i jest używana do inicjowania jego zawartości, w tym dowolnej z jego formantów.

Poniższy przykład kodu używa *zmiennej m_circctl* elementu członkowskiego do modyfikowania caption i CircleShape właściwości osadzonego formantu Circ:

[!code-cpp[NVC_MFC_AxCont#7](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_7.cpp)]

## <a name="see-also"></a>Zobacz też

[Kontenery kontrolek ActiveX](../mfc/activex-control-containers.md)
