---
title: Określanie formantu dominującego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dominant controls
- Dialog editor, dominant control
- controls [C++], dominant
ms.assetid: 42b523a7-192a-417b-9512-d4af795e002f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 93e8d1dff23d77d861a52d4f1531203ebd05987b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593299"
---
# <a name="specifying-the-dominant-control"></a>Określanie formantu dominującego

Wybraną kontrolkę jest najpierw formantu dominującego.

### <a name="to-specify-the-dominant-control"></a>Aby określić formant dominujący

1. Naciśnij i przytrzymaj **Ctrl** klucza i kliknij formant, którego chcesz użyć do wywierania wpływu na rozmiar lub lokalizację innych formantów *pierwszy*.

   **Uwaga** uchwyty zmiany rozmiaru formantu dominującego są wypełnione uchwytów kontrolki podrzędne są puste. Dalsze zmiany rozmiaru lub wyrównanie opiera się na formant dominujący.

### <a name="to-change-the-dominant-control"></a>Aby zmienić kontrolki dominującej

1. Wyczyść bieżący wybór, klikając poza wszystkie obecnie wybrane formanty.

2. Powtórz poprzedniej procedury, wybierając najpierw innej kontrolki.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Wybieranie wielu kontrolek](../windows/selecting-multiple-controls.md)  
[Zaznaczanie kontrolek](../windows/selecting-controls.md)  
[Kontrolki w oknach dialogowych](../windows/controls-in-dialog-boxes.md)