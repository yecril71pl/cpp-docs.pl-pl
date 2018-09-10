---
title: Właściwości poleceń menu (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- menu items, properties
ms.assetid: 6d308205-3c9e-42f2-ab42-45e656940e45
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 28426e2ca75638f5ad45188a8790d1c281afa99b
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44317924"
---
# <a name="menu-command-properties-c"></a>Właściwości poleceń menu (C++)

Poniższe informacje są organizowane według **Menu** właściwości, które pojawiają się w [okno właściwości](/visualstudio/ide/reference/properties-window) po wybraniu polecenia menu. Te są wymieniane alfabetycznie mimo że **właściwości** okno umożliwia również wyświetlanie tych właściwości według kategorii.

|Właściwość|Opis|
|--------------|-----------------|
|**BREAK**|Może być jedną z następujących wartości:<br /><br /> -   **Brak** (opcja domyślna): bez przerwy.<br />-   **Kolumna**: statyczne menu, ta wartość umieszcza polecenie menu w nowym wierszu. Ta wartość wyskakujących menu umieszcza polecenia menu w nową kolumnę z nie jednoznaczny kolumn. Ustawienie tej właściwości ma wpływ na wygląd menu tylko w czasie wykonywania, nie Edytor menu.<br />-   **Pasek**: taki sam jak **kolumny** z wyjątkiem sytuacji, menu podręczne tę wartość oddziela nowej kolumny od starego kolumnę z pionowym wierszem. Ustawienie tej właściwości określa wygląd menu tylko w czasie wykonywania, nie w **Menu** edytora.|
|**Podpis**|Tekst etykiety polecenia menu (Nazwa menu). Aby utworzyć kolekcję liter w podpisie menu poleceń klawisz dostępu, należy poprzedzić handlowe "i" (&).|
|**Zaznaczone**|Jeśli **True**, polecenia menu jest domyślnie zaznaczone. Typ: **Bool**. Wartość domyślna: **False**.|
|**Włączone**|Jeśli **False**, element menu jest wyłączona.|
|**Wyszarzony**|Jeśli **True**, polecenia menu jest początkowo wygaszone i nieaktywnych. Typ: **Bool**. Wartość domyślna: **False**.|
|**Pomoc**|Wyrównuje elementu menu z prawej strony. Na przykład **pomocy** polecenia menu jest zawsze po prawej stronie we wszystkich aplikacjach Windows. Jeśli ustawisz tę właściwość, element menu, ten element pojawi się po bardzo prawej stronie i na końcu menu. Dotyczy to elementów najwyższego poziomu. Wartość domyślna: **False**.|
|**ID**|Symbol zdefiniowany w pliku nagłówkowym. Typ: **Symbol**, **całkowitą**, lub **ciąg w cudzysłowach**. Może używać dowolny symbol, który jest powszechnie dostępne we wszystkich edytory, nawet jeśli [okno właściwości](/visualstudio/ide/reference/properties-window) nie zawiera listy rozwijanej, wybierz z.|
|**Popup**|Jeśli **True**, polecenia menu jest menu podręczne. Typ: **Bool**. Wartość domyślna: **True** menu najwyższego poziomu w menu paska; w przeciwnym razie **False**.|
|**wiersz**|Zawiera tekst wyświetlany na pasku stanu wyróżnionego to polecenie menu. Tekst jest umieszczany w tabeli ciągów zawierających ten sam identyfikator jak polecenie menu. Ta właściwość jest dostępna dla wszystkich typów projektów, ale funkcje środowiska wykonawczego jest określone MFC.|
|**Wyjustuj do prawej do lewej**|Po prawej stronie uzasadnia polecenia menu na pasku menu w czasie wykonywania. Typ: **Bool**. Wartość domyślna: **False**.|
|**Od prawej do lewej kolejności**|Umożliwia polecenia menu wyświetlić od prawej do lewej, gdy interfejs jest zlokalizowane dla dowolnego języka, który odczytuje prawej do lewej, takich jak hebrajskiego i arabskiego.|
|**Separator**|Jeśli **True**, polecenia menu jest separatorem. Typ: **Bool**. Wartość domyślna: **False**.|

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Edytor menu](../windows/menu-editor.md)