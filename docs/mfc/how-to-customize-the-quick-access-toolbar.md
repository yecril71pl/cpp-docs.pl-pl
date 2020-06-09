---
title: 'Porady: dostosowywanie paska narzędzi Szybki dostęp'
ms.date: 09/07/2019
helpviewer_keywords:
- quick access toolbar [MFC], customization
ms.assetid: 2554099b-0c89-4605-9249-31bf9cbcefe0
ms.openlocfilehash: 5d168fc395e27eea3705fc8e69c88569ecb0f7ee
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620033"
---
# <a name="how-to-customize-the-quick-access-toolbar"></a>Porady: dostosowywanie paska narzędzi Szybki dostęp

Pasek narzędzi Szybki dostęp (QAT) to dostosowywalny pasek narzędzi zawierający zestaw poleceń, które są wyświetlane obok przycisku aplikacji lub na kartach kategorie. Na poniższej ilustracji przedstawiono typowy pasek narzędzi Szybki dostęp.

![Pasek narzędzi szybkiego dostępu do wstążki MFC](../mfc/media/quick_access_toolbar.png "Pasek narzędzi szybkiego dostępu do wstążki MFC")

Aby dostosować pasek narzędzi Szybki dostęp, otwórz go w oknie **Właściwości** , zmodyfikuj jego polecenia, a następnie Wyświetl podgląd kontrolki wstążki.

### <a name="to-open-the-quick-access-toolbar-in-the-properties-window"></a>Aby otworzyć pasek narzędzi Szybki dostęp w okno Właściwości

1. W programie Visual Studio, w menu **Widok** kliknij **Widok zasobów**.

1. W **Widok zasobów**kliknij dwukrotnie zasób wstążki, aby wyświetlić go na powierzchni projektowej.

1. Na powierzchni projektowej kliknij prawym przyciskiem myszy menu paska narzędzi Szybki dostęp, a następnie kliknij polecenie **Właściwości**.

## <a name="quick-access-toolbar-properties"></a>Właściwości paska narzędzi Szybki dostęp

Poniższa tabela zawiera definicje właściwości paska narzędzi Szybki dostęp.

|Właściwość|Definicja|
|--------------|----------------|
|Pozycja QAT|Określa pozycję paska narzędzi Szybki dostęp podczas uruchamiania aplikacji. Pozycja może być albo **powyżej** , albo **poniżej** kontrolki wstążki.|
|Elementy QAT|Określa polecenia, które są dostępne dla paska narzędzi Szybki dostęp.|

#### <a name="to-add-or-remove-commands-on-the-quick-access-toolbar"></a>Aby dodać lub usunąć polecenia na pasku narzędzi Szybki dostęp

1. W oknie **Właściwości** kliknij pozycję **QAT elementy**, a następnie kliknij przycisk wielokropka **(...)**.

1. W oknie dialogowym **Edytor elementów QAT** Użyj przycisków **Dodaj** i **Usuń** , aby zmodyfikować listę poleceń na pasku narzędzi Szybki dostęp.

1. Jeśli chcesz, aby polecenie pojawiało się zarówno na pasku narzędzi Szybki dostęp, jak i w menu paska narzędzi Szybki dostęp, zaznacz pole obok polecenia. Jeśli chcesz, aby polecenie było wyświetlane tylko w menu, wyczyść pole wyboru.

## <a name="previewing-the-ribbon"></a>Wyświetlanie podglądu wstążki

Polecenia paska narzędzi Szybki dostęp nie są wyświetlane na powierzchni projektowej. Aby je wyświetlić, należy wyświetlić podgląd wstążki lub uruchomić aplikację.

#### <a name="to-preview-the-ribbon-control"></a>Aby wyświetlić podgląd kontrolki wstążki

- Na **pasku narzędzi edytora wstążki**kliknij pozycję **Testuj wstążka**.

## <a name="see-also"></a>Zobacz też

[Projektant wstążki (MFC)](ribbon-designer-mfc.md)
