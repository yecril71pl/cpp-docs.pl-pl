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
- status bars [C++], associating menu items
- menus [C++], status bar text
ms.assetid: 757c0e02-bc97-493f-bccd-6cc6887ebc64
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 16de276478485cb52b11b3f1bbb869c5b75d05a4
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44316760"
---
# <a name="associating-menu-commands-with-status-bar-text-in-mfc-applications"></a>Kojarzenie poleceń menu z tekstem paska stanu w aplikacjach MFC

Aplikacja MFC można wyświetlić tekst opisu dla każdego polecenia menu, które użytkownik może wybrać. Możesz to zrobić, przypisując ciąg tekstowy do każdego menu polecenia przy użyciu **monitu** właściwość **właściwości** okna. Jeśli w ciągu [tabeli ciągów](../windows/string-editor.md) których identyfikator jest taki sam jak polecenia, aplikacji MFC będą automatycznie wyświetlać ten zasób ciąg w pasku stanu w uruchomionej aplikacji po użytkownik myszy nad element menu.

### <a name="to-associate-a-menu-command-with-a-status-bar-text-string"></a>Aby skojarzyć polecenia menu z stanu paska ciąg tekstowy

1. W **Menu** edytora, wybierz polecenie menu.

2. W [okno właściwości](/visualstudio/ide/reference/properties-window), wpisz tekst skojarzony z nim stan paska w **monitu** pole.

## <a name="requirements"></a>Wymagania

MFC

## <a name="see-also"></a>Zobacz też

[Ciągi (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)  
[Dodawanie poleceń do menu](../windows/adding-commands-to-a-menu.md)  
[Edytor menu](../windows/menu-editor.md)