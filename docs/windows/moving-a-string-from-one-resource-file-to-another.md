---
title: Przenoszenie ciągu z jednego pliku zasobu do innego (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- strings [C++], moving between files
- resource script files [C++], moving strings
- string editing, moving strings between resources
- String editor [C++], moving strings between files
ms.assetid: 94f8ee81-9b4c-4788-ba95-68c58db38029
ms.openlocfilehash: e89a0d44dc824c72710f8a047a18771ba8da492b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50649817"
---
# <a name="moving-a-string-from-one-resource-file-to-another-c"></a>Przenoszenie ciągu z jednego pliku zasobu do innego (C++)

### <a name="to-move-a-string-from-one-resource-script-file-to-another"></a>Aby przenieść pliku skryptu zasobu w jeden ciąg

1. Otwórz w tabelach ciągów w obu plikach .rc. (Aby uzyskać więcej informacji, zobacz [wyświetlania zasobów w zasobu skryptu pliku poza z projektem](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).)

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

2. Kliknij prawym przyciskiem myszy ciągu chcesz przenieść, a następnie wybierz **Wytnij** z menu skrótów.

3. Umieść kursor w miejscu docelowym **edytor ciągów** okna.

4. W pliku .rc, do którego chcesz przenieść ciągu, kliknij prawym przyciskiem myszy i wybierz polecenie **Wklej** z menu skrótów.

   > [!NOTE]
   > Jeśli **identyfikator** lub **wartość** konfliktów ciągu przeniesione z istniejącym **identyfikator** lub **wartość** w pliku docelowym, albo **Identyfikator** lub **wartość** zmian przeniesionych ciągu. Jeśli ciąg istnieje z tym samym **identyfikator**, **identyfikator** zmian przeniesionych ciągu. Jeśli ciąg istnieje z tym samym **wartość**, **wartość** zmian przeniesionych ciągu.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, (te, których platformą docelową środowiska uruchomieniowego języka wspólnego), zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Instruktaż: Lokalizowanie interfejsów Windows Forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Edytor ciągów](../windows/string-editor.md)<br/>
[Pliki zasobów](../windows/resource-files-visual-studio.md)<br/>
[Dostosowywanie układów okien](/visualstudio/ide/customizing-window-layouts-in-visual-studio)