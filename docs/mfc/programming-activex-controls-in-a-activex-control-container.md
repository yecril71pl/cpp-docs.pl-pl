---
title: 'Kontenery kontrolek ActiveX: Programowanie kontrolek ActiveX w kontenerze kontrolek ActiveX | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6f83b0d947fbc663bce50eac7887904816e1afbe
ms.sourcegitcommit: a3c9e7888b8f437a170327c4c175733ad9eb0454
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2018
ms.locfileid: "50204460"
---
# <a name="activex-control-containers-programming-activex-controls-in-an-activex-control-container"></a>Kontenery kontrolek ActiveX: programowanie kontrolek ActiveX w kontenerze kontrolek ActiveX

W tym artykule opisano proces uzyskiwania dostępu do narażonych [metody](../mfc/mfc-activex-controls-methods.md) i [właściwości](../mfc/mfc-activex-controls-properties.md) osadzone formantów ActiveX.

>[!IMPORTANT]
> ActiveX jest technologią starszą, która nie powinny być używane w przypadku nowych wdrożeń. Aby uzyskać więcej informacji na temat nowych technologii, które zastępują ActiveX zobacz [formantów ActiveX](activex-controls.md).

Będzie po prostu wykonaj następujące kroki:

1. [Wstaw kontrolkę ActiveX do projektu ActiveX w kontenerze](../mfc/inserting-a-control-into-a-control-container-application.md) przy użyciu galerii.

1. [Zdefiniuj zmienną członkowską](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md) (lub inną formę dostępu) z tego samego typu co ActiveX kontrolować klasy otoki.

1. [Program formantu ActiveX](#_core_programming_the_activex_control) przy użyciu wstępnie zdefiniowane funkcje Członkowskie klasy otoki.

Na potrzeby tego omówienia przyjęto założenie, że utworzono projektu oparte o okna dialogowe (o nazwie kontenera) przy użyciu obsługi formantów ActiveX. Pełna kontrola przykładowe OK i OK, zostaną dodane do wynikowego projektu.

Po wstawieniu kontrolki OK do projektu (krok 1) należy wstawić wystąpienie kontrolki OK do głównego okna dialogowego aplikacji.

## <a name="procedures"></a>Procedury

#### <a name="to-add-the-circ-control-to-the-dialog-template"></a>Aby dodać formant OK do szablonu okna dialogowego

1. Załaduj projekt kontener formantu ActiveX. W tym przykładzie użyj `Container` projektu.

1. Kliknij kartę widoku zasobów.

1. Otwórz **okna dialogowego** folderu.

1. Kliknij dwukrotnie szablonu okna dialogowego głównego. W tym przykładzie użyj **IDD_CONTAINER_DIALOG**.

1. Kliknij ikonę kontrolki OK w przyborniku.

1. Kliknij punkt, w oknie dialogowym, aby wstawić formant OK.

1. Z **pliku** menu, wybierz **Zapisz wszystko** Aby zapisać wszystkie zmiany do szablonu okna dialogowego.

## <a name="modifications-to-the-project"></a>Modyfikacje projektu

Aby umożliwić aplikacji kontenera uzyskać dostęp do formantu OK, Visual C++ automatycznie dodaje klasy otoki (`CCirc`) pliku implementacji (. CPP) do projektu kontenera i nagłówek klasy otoki (. H) pliku do pliku nagłówka okno dialogowe:

[!code-cpp[NVC_MFC_AxCont#1](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_1.h)]

##  <a name="_core_the_wrapper_class_header_28h29_file"></a> Nagłówek klasy otoki (. H) plik

Aby uzyskać i ustawić właściwości (i wywoływać metody) dla formantu OK `CCirc` klasy otoki zawiera deklarację narażonych wszystkie metody i właściwości. W tym przykładzie te deklaracje znajdują się w okólnik H. Poniższy przykład jest to część klasy `CCirc` definiujący interfejsów formantu ActiveX:

[!code-cpp[NVC_MFC_AxCont#2](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_2.h)]
[!code-cpp[NVC_MFC_AxCont#3](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_3.h)]

Te funkcje można następnie wywołać innej procedury aplikacji przy użyciu normalnych składni języka C++. Aby uzyskać więcej informacji na temat korzystania z tej funkcji elementu członkowskiego, ustaw na dostęp do metod i właściwości formantu, zobacz sekcję [programowanie kontrolek ActiveX](#_core_programming_the_activex_control).

##  <a name="_core_member_variable_modifications_to_the_project"></a> Element członkowski modyfikacje zmiennych do projektu

Gdy formant ActiveX zostanie dodany do projektu i osadzone w kontenerze okno dialogowe, uzyskiwania dostępu przez inne części projektu. Najprostszym sposobem, aby uzyskać dostęp do formantu jest [Utwórz zmienną składową](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md) klasy okna dialogowego `CContainerDlg` (krok 2), czyli z tego samego typu co klasa otoki dodane do projektu przez Visual C++. Następnie można zmiennej składowej dostęp do formantu osadzonego w dowolnym momencie.

Gdy **Dodawanie zmiennej członkowskiej** dodaje okno dialogowe *m_circctl* składowej zmiennej do projektu dodano również następujące wiersze do pliku nagłówka (. Godz.) z `CContainerDlg` klasy:

[!code-cpp[NVC_MFC_AxCont#4](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_4.h)]
[!code-cpp[NVC_MFC_AxCont#5](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_5.h)]

Ponadto wywołanie **ddx_control —** jest automatycznie dodawany do `CContainerDlg`przez implementację `DoDataExchange`:

[!code-cpp[NVC_MFC_AxCont#6](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_6.cpp)]

##  <a name="_core_programming_the_activex_control"></a> Programowanie kontrolek ActiveX

W tym momencie masz dodaje formant ActiveX do szablonu okna dialogowego i utworzono zmienną składową. Typowej składni języka C++ umożliwia teraz dostęp do właściwości i metod formantu osadzonego.

Jak wspomniano (w [nagłówka klasy otoki (. Plik H)](#_core_the_wrapper_class_header_28h29_file)), plik nagłówkowy (. H) aby `CCirc` klasy otoki, w tym okólnik wielkości liter Godz., zawiera listę funkcji Członkowskich, które umożliwia pobieranie i ustawianie dowolnej wartości właściwości narażone. Dostępne są również funkcji elementów członkowskich dla narażonych metod.

Typowe miejscem, aby zmodyfikować właściwości formantu jest `OnInitDialog` funkcji składowej klasy głównego okna dialogowego. Ta funkcja jest wywoływana tuż przed okno dialogowe pojawia się i służy do inicjowania jego zawartość, wraz ze wszystkimi jego środków kontroli.

Poniższy przykład kodu wykorzystuje *m_circctl* zmiennej składowej, aby zmodyfikować właściwości podpisu i CircleShape formantu osadzonego OK:

[!code-cpp[NVC_MFC_AxCont#7](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_7.cpp)]

## <a name="see-also"></a>Zobacz też

[Kontenery kontrolek ActiveX](../mfc/activex-control-containers.md)

