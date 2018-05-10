---
title: Właściwości poleceń menu | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 343c1ce255a26753c2b125d2a0a53e04808a0233
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="menu-command-properties"></a>Właściwości poleceń menu
Poniższe informacje są zorganizowane według właściwości Menu, które są widoczne w [okna właściwości](/visualstudio/ide/reference/properties-window) po wybraniu polecenia menu. Wyliczono alfabetycznie okna właściwości umożliwia również wyświetlić te właściwości według kategorii.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|**Podziel**|Może być jedną z następujących wartości:<br /><br /> -   **Brak** (domyślna): bez przerwy.<br />-   **Kolumna**: menu statyczne, ta wartość umieszcza polecenie w nowym wierszu. Menu wyskakujące ta wartość umieszcza polecenia menu w nową kolumnę z Brak linii podziału między kolumnami. Ustawienie tej właściwości określa wygląd menu tylko w czasie wykonywania, nie w edytorze menu.<br />-   **Pasek**: taki sam jak kolumna z wyjątkiem menu podręczne, nowej kolumny, która oddziela tej wartości od starego kolumna z linią pionową. Ustawienie tej właściwości określa wygląd menu tylko w czasie wykonywania, nie w edytorze Menu.|  
|**Podpis**|Tekst etykiety menu polecenie (Nazwa menu). Aby jedną z liter w podpisie menu polecenie klawisz skrótu, należy poprzedzić handlowego "i" (&).|  
|**Zaznaczone**|Jeśli PRAWDA, to polecenie jest domyślnie zaznaczone. Typ: wartość logiczna. Domyślnie: False.|  
|**włączone**|Jeśli **False**, element menu jest wyłączony.|  
|**Wyszarzony**|Jeśli PRAWDA, polecenia menu jest początkowo wygaszone i nieaktywne. Typ: wartość logiczna. Domyślnie: False.|  
|**Pomoc**|Wyrównuje element menu z prawej strony. Na przykład **pomocy** polecenie jest zawsze po prawej stronie we wszystkich aplikacjach systemu Windows. Jeśli ta właściwość jest ustawiona na element menu, element pojawi się bardzo prawej i na końcu menu. Dotyczy elementów najwyższego poziomu. Wartość domyślna: **False**.|  
|**ID**|Symbol zdefiniowany w pliku nagłówka. Typ: Symbol, liczbą całkowitą lub ciągu w cudzysłowie. Możesz użyć dowolnego symbol, który jest powszechnie dostępna w żadnym z edytora, nawet jeśli [okna właściwości](/visualstudio/ide/reference/properties-window) nie ma do wyboru z listy rozwijanej.|  
|**Popup**|Jeśli PRAWDA, to polecenie jest menu podręczne. Typ: wartość logiczna. Domyślnie: True dla najwyższego poziomu menu na pasku menu; w przeciwnym razie wartość False.|  
|**wiersz**|Zawiera tekst wyświetlany na pasku stanu, jeśli polecenie zostanie wyróżniona. Tekst jest umieszczany w tabeli ciągów o tym samym identyfikatorze jak polecenie menu. Ta właściwość jest dostępna dla dowolnego typu projektu, ale funkcje czasu wykonywania jest określonych MFC.|  
|**Wyjustuj od prawej do lewej**|Wyrównuje prawo polecenia menu na pasku menu w czasie wykonywania. Typ: wartość logiczna. Domyślnie: False.|  
|**Od prawej do lewej kolejności**|Umożliwia polecenia menu mają być wyświetlane od prawej do lewej, gdy interfejs jest zlokalizowane dla dowolnego języka, który odczytuje prawej do lewej, takich jak hebrajski lub arabski.|  
|**Separator**|Jeśli PRAWDA, to polecenie jest separatora. Typ: wartość logiczna. Domyślnie: False.|  
  

  
## <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Edytor menu](../windows/menu-editor.md)