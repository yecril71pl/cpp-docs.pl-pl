---
title: Kojarzenie poleceń Menu z tekstem paska stanu w aplikacjach MFC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- status bars, associating menu items
- menus, status bar text
ms.assetid: 757c0e02-bc97-493f-bccd-6cc6887ebc64
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d9cb5e57d6c7020e0b89104dac87fa3cd08ea023
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42583704"
---
# <a name="associating-menu-commands-with-status-bar-text-in-mfc-applications"></a>Kojarzenie poleceń menu z tekstem paska stanu w aplikacjach MFC

Aplikacja może wyświetlać tekst opisu dla każdego polecenia menu, które użytkownik może wybrać. Możesz to zrobić, przypisując ciąg tekstowy do każdego menu polecenia przy użyciu **monitu** właściwość **właściwości** okna. Jeśli w ciągu [tabeli ciągów](../windows/string-editor.md) których identyfikator jest taki sam jak polecenia, aplikacji MFC będą automatycznie wyświetlać ten zasób ciąg w pasku stanu w uruchomionej aplikacji po użytkownik myszy nad element menu.

### <a name="to-associate-a-menu-command-with-a-status-bar-text-string"></a>Aby skojarzyć polecenia menu z stanu paska ciąg tekstowy

1. W **Menu** edytora, wybierz polecenie menu.

2. W [okno właściwości](/visualstudio/ide/reference/properties-window), wpisz tekst skojarzony z nim stan paska w **monitu** pole.

## <a name="requirements"></a>Wymagania

MFC

## <a name="see-also"></a>Zobacz też

[Ciągi (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)  
[Dodawanie poleceń do menu](../windows/adding-commands-to-a-menu.md)  
[Edytor menu](../windows/menu-editor.md)