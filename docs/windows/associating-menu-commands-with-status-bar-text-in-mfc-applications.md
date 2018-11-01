---
title: Kojarzenie poleceń menu z tekstem paska stanu w aplikacjach MFC
ms.date: 11/04/2016
helpviewer_keywords:
- status bars [C++], associating menu items
- menus [C++], status bar text
ms.assetid: 757c0e02-bc97-493f-bccd-6cc6887ebc64
ms.openlocfilehash: fc39695358a9c1f2f62878487a5e4fedf5db2b82
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468890"
---
# <a name="associating-menu-commands-with-status-bar-text-in-mfc-applications"></a>Kojarzenie poleceń menu z tekstem paska stanu w aplikacjach MFC

Aplikacja MFC można wyświetlić tekst opisu dla każdego polecenia menu, które użytkownik może wybrać. Możesz to zrobić, przypisując ciąg tekstowy do każdego menu polecenia przy użyciu **monitu** właściwość **właściwości** okna. Jeśli w ciągu [tabeli ciągów](../windows/string-editor.md) których identyfikator jest taki sam jak polecenia, aplikacji MFC będą automatycznie wyświetlać ten zasób ciąg w pasku stanu w uruchomionej aplikacji po użytkownik myszy nad element menu.

### <a name="to-associate-a-menu-command-with-a-status-bar-text-string"></a>Aby skojarzyć polecenia menu z stanu paska ciąg tekstowy

1. W **Menu** edytora, wybierz polecenie menu.

2. W [okno właściwości](/visualstudio/ide/reference/properties-window), wpisz tekst skojarzony z nim stan paska w **monitu** pole.

## <a name="requirements"></a>Wymagania

MFC

## <a name="see-also"></a>Zobacz też

[Ciągi (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[Dodawanie poleceń do menu](../windows/adding-commands-to-a-menu.md)<br/>
[Edytor menu](../windows/menu-editor.md)