---
title: 'Porady: dostosowywanie paska narzędzi Szybki dostęp'
ms.date: 11/04/2016
helpviewer_keywords:
- quick access toolbar [MFC], customization
ms.assetid: 2554099b-0c89-4605-9249-31bf9cbcefe0
ms.openlocfilehash: d9bdc523218c7fad217d066eabd518aaff011df3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50558486"
---
# <a name="how-to-customize-the-quick-access-toolbar"></a>Porady: dostosowywanie paska narzędzi Szybki dostęp

Szybki dostęp do paska narzędzi (QAT) jest paskiem narzędzi, który zawiera zestaw poleceń, które są albo wyświetlane obok przycisku aplikacji lub w ramach karty kategorii. Poniższa ilustracja przedstawia typowy narzędzi Szybki dostęp.

![MFC wstążce paska narzędzi szybkiego dostępu](../mfc/media/quick_access_toolbar.png "quick_access_toolbar")

Aby dostosować paska narzędzi Szybki dostęp, otwórz go w **właściwości** , zmodyfikuj jego poleceń, a następnie Wyświetl podgląd formantu wstążki.

### <a name="to-open-the-quick-access-toolbar-in-the-properties-window"></a>Aby otworzyć pasek narzędzi Szybki dostęp w oknie dialogowym właściwości

1. W programie Visual Studio na **widoku** menu, kliknij przycisk **widok zasobów**.

1. W **widok zasobów**, kliknij dwukrotnie zasób wstążki, aby wyświetlić je na powierzchni projektowej.

1. Na powierzchni projektowej kliknij prawym przyciskiem myszy menu paska narzędzi Szybki dostęp, a następnie kliknij przycisk **właściwości**.

## <a name="quick-access-toolbar-properties"></a>Właściwości paska narzędzi Szybki dostęp

W poniższej tabeli opisano właściwości paska narzędzi Szybki dostęp.

|Właściwość|Definicja|
|--------------|----------------|
|Położenie QAT|Określa położenie paska narzędzi Szybki dostęp, podczas uruchamiania aplikacji. Pozycja może być **powyżej** lub **poniżej** formantu wstążki.|
|Elementy QAT|Określa polecenia, które są dostępne dla paska narzędzi Szybki dostęp.|

#### <a name="to-add-or-remove-commands-on-the-quick-access-toolbar"></a>Aby dodać lub usunąć polecenia na pasku narzędzi Szybki dostęp

1. W **właściwości** okna, kliknij przycisk **elementy QAT**, a następnie kliknij przycisk wielokropka **(...)** .

1. W **Edytor elementów QAT** okno dialogowe, użyj **Dodaj** i **Usuń** przycisków, aby zmodyfikować listę poleceń na pasku narzędzi Szybki dostęp.

1. Zaznacz pole wyboru obok polecenia, polecenie, aby się na pasku narzędzi Szybki dostęp i menu paska narzędzi Szybki dostęp. Jeśli chcesz umieścić tylko z menu polecenie, wyczyść pole.

## <a name="previewing-the-ribbon"></a>Wyświetlanie podglądu wstążki

Szybkie polecenia narzędzi dostęp nie jest wyświetlana na powierzchni projektowej. Aby je wyświetlić, możesz przeglądanie Wstążki lub uruchomić aplikację.

#### <a name="to-preview-the-ribbon-control"></a>Aby wyświetlić podgląd formantu wstążki

- Na **pasek narzędzi edytora wstążki**, kliknij przycisk **Testuj Wstążkę**.

## <a name="see-also"></a>Zobacz też

[Projektant wstążki (MFC)](../mfc/ribbon-designer-mfc.md)

