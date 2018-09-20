---
title: Ustalanie rozmiaru pojedynczych formantów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Size to Content command
- size, controls
- text, autosizing controls to fit text
- controls [C++], sizing
ms.assetid: 14ccba02-7171-463a-a121-7018cf1e2e5a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9932b14b3d3afaa0afdff90c08ce44bf1f8648dc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373481"
---
# <a name="sizing-individual-controls"></a>Ustalanie rozmiaru pojedynczych formantów

Zmień rozmiar kontrolki za pomocą uchwytów zmiany rozmiaru. Po umieszczeniu wskaźnika na uchwyt zmiany rozmiaru, zmienia kształt, aby wskazać kierunki, w których kontrolki można zmienić rozmiar. Uchwyty zmiany rozmiaru Active są wypełnione; Jeśli uchwyt zmiany rozmiaru jest pusty, formant nie można zmienić rozmiaru na tej osi.

Możesz również zmienić rozmiar formantu przez przyciągania formant do prowadnic i marginesów lub przenosząc jeden przypięty kontroli i przewodnik od innego.

### <a name="to-size-a-control"></a>Rozmiar kontrolki

1. Zaznacz formant.

2. Przeciągnij uchwyty zmiany rozmiaru, aby zmienić rozmiar formantu:

   - Uchwyty zmiany rozmiaru u góry i strony Zmień rozmiar poziomej lub pionowej.

   - Uchwyty zmiany rozmiaru w rogach Zmień rozmiar zarówno w poziomie, jak i w pionie.

   > [!TIP]
   > Możesz zmienić rozmiar formantu jednostki jednego okna dialogowego (DLU) w danym momencie, przytrzymując **Shift** kluczy i korzystać z funkcji **Strzałka w prawo** i **strzałkę w dół** kluczy.

### <a name="to-automatically-size-a-control-to-fit-the-text-within-it"></a>Aby automatycznie rozmiar formantu do tekstu w nim

1. Wybierz **rozmiar do zawartości** z **Format** menu.

\- lub —

- Kliknij prawym przyciskiem myszy formant, a następnie wybierz **rozmiar do zawartości** z menu skrótów.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Kontrolki w oknach dialogowych](../windows/controls-in-dialog-boxes.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)