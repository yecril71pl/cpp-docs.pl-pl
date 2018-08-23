---
title: Okienka (edytor obrazów dla ikon) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
dev_langs:
- C++
helpviewer_keywords:
- graphics editor [C++]
- Image editor [C++], panes
ms.assetid: d66ea5b3-e2e2-4fc4-aa99-f50022cc690e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 02cc8fed4056199787c3108d287945bb8a0ae7dd
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42594109"
---
# <a name="window-panes-image-editor-for-icons"></a>Okienka (Edytor obrazów dla ikon)

**Edytora obrazów** okna zwykle wyświetla obraz na dwa okienka rozdzielone pasek podziału. Jeden widok jest rzeczywisty rozmiar, a druga powiększenia (domyślny współczynnik rozszerzenia jest 6). Widoki te dwa okienka są automatycznie aktualizowane: zmiany wprowadzone w jednym okienku natychmiast są wyświetlane w innym. Dwa okienka ułatwiają pracować nad powiększania widoku obrazu, w którym można odróżnić poszczególnych pikseli i, w tym samym czasie obserwować wpływ swoją pracę na widoku rzeczywisty rozmiar obrazu.

Tyle miejsca, ile potrzeba korzysta z okienka po lewej stronie (do połowy **obraz** okna) do wyświetlenia widoku powiększeniem 1:1 (opcja domyślna) obrazu. W okienku po prawej stronie wyświetla powiększonego (6:1 powiększenie domyślnie). Możesz [zmiana powiększenia](../windows/changing-the-magnification-factor-image-editor-for-icons.md) w każdym za pomocą okienka **Magnify** narzędzie [paska narzędzi edytora obrazów](../windows/toolbar-image-editor-for-icons.md) lub za pomocą klawiszy skrótów.

Można powiększyć mniejszych okienku **edytora obrazów** okno i użyj dwa okienka, aby pokazać różnych regionach duży obraz. Kliknij w okienku, aby go zaznaczyć.

Względne rozmiary okienek można zmienić, ustawiając kursor na pasek podziału i przenoszenie pasek podziału w prawo lub lewo. Pasek podziału można przenieść do dowolnej stronie, aby pracować nad tylko jedno okienko.

Jeśli **edytora obrazów** okienko jest powiększony o 4 lub nowszej, możesz [wyświetlić siatkę pikseli](../windows/displaying-or-hiding-the-pixel-grid-image-editor-for-icons.md) który rozgranicza piksele na obrazie.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz też

[Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)  
[Edytor obrazów dla ikon](../windows/image-editor-for-icons.md)