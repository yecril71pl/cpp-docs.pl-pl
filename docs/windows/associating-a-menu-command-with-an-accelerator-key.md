---
title: Kojarzenie polecenia Menu z klawiszem skrótu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- keyboard shortcuts, menu association
- commands, associating menu commands with accelerator keys
- menu commands, associating with keyboard shortcuts
ms.assetid: ad2de43f-b20a-4c9f-bda8-0420179da48c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5b1411617df3736300536e84e07da0bb5df3a856
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42599953"
---
# <a name="associating-a-menu-command-with-an-accelerator-key"></a>Kojarzenie polecenia menu z klawiszem skrótu

Są często razy polecenia menu a kombinacja klawiszy, Wydaj to samo polecenie program. Możesz to zrobić przy użyciu **Menu** edytora, aby przypisać ten sam identyfikator zasobu, do polecenia menu i wpis w tabeli klawiszy skrótu aplikacji. Następnie Edytuj [podpis](../windows/menu-command-properties.md) polecenia menu, aby wyświetlić nazwę klawisza skrótu.

### <a name="to-associate-a-menu-command-with-an-accelerator-key"></a>Aby skojarzyć polecenia menu z klawiszem skrótu

1. W **Menu** edytora, wybierz polecenia menu, które ma.

2. W [okno właściwości](/visualstudio/ide/reference/properties-window), Dodaj nazwę klawisza skrótu do **podpis** właściwości:

   - Następujący podpis menu Typ sekwencji ucieczki dla karty (\t) tak, aby wszystkie klawisze skrótów menu są pozostawiane wyrównane.

   - Wpisz nazwę klawisz modyfikujący (**Ctrl**, **Alt**, lub **Shift**) ze znakiem plus (**+**) i nazwę, litery, lub symbol dodatkowy klucz.

       Na przykład, aby przypisać **Ctrl**+**O** do **Otwórz** polecenie **pliku** menu modyfikowanie polecenia menu  **Podpis** tak, aby wygląda następująco:

        ```
        &Open...\tCtrl+O
        ```

       Polecenia menu w **Menu** edytora jest aktualizowana w celu odzwierciedlenia nowy podpis w trakcie pisania.

3. [Tworzenie wpisu tabeli akceleratora](../windows/adding-an-entry-to-an-accelerator-table.md) w **akceleratora** edytora i przypisać ją w taki sam identyfikator jak polecenie menu. Użyj kombinacji klawiszy, które uważasz, że będzie łatwa do zapamiętania.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Dodawanie poleceń do menu](../windows/adding-commands-to-a-menu.md)  
[Edytor menu](../windows/menu-editor.md)