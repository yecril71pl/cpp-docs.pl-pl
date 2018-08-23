---
title: Wstawianie kontrolki ActiveX, okno dialogowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.dialog.insertActiveXControls
dev_langs:
- C++
helpviewer_keywords:
- Insert ActiveX Control dialog box
- ActiveX controls [C++], adding to dialog boxes
ms.assetid: 06638ea3-0726-40da-a989-9b89292d0e3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6e9f14b696ff67b52c365617682c0cc4c43432cd
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42602819"
---
# <a name="insert-activex-control-dialog-box"></a>Wstawianie kontrolki ActiveX — Okno dialogowe

To okno dialogowe umożliwia [wstawić formanty ActiveX do dialogowym](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md) podczas korzystania z [Edytor okien dialogowych](../windows/dialog-editor.md).

### <a name="activex-control"></a>Kontrolki ActiveX

Wyświetla listę formantów ActiveX. Wstawianie kontrolki z tego okna dialogowego nie generuje klasę otoki. Klasa otoki, należy użyć [Widok klas](http://msdn.microsoft.com/8d7430a9-3e33-454c-a9e1-a85e3d2db925) ją utworzyć (Aby uzyskać więcej informacji, zobacz [Dodawanie klasy](../ide/adding-a-class-visual-cpp.md)). Jeśli formant ActiveX nie ma w tym oknie dialogowym, spróbuj zainstalować kontroli zgodnie z instrukcjami dostawcy.

### <a name="path"></a>Ścieżka

Wyświetla plik, w którym znajduje się Kontrolka ActiveX.

Możesz umieścić formantów w **przybornika** okna, aby mieć łatwy dostęp. Aby uzyskać więcej informacji, zobacz [dostosowywania przybornika, okno dialogowe](http://msdn.microsoft.com/bd07835f-18a8-433e-bccc-7141f65263bb).

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Karta Edytor okien dialogowych, Przybornik](../windows/dialog-editor-tab-toolbox.md)  
[Pliki zasobów](../windows/resource-files-visual-studio.md)  
[Kontrolki w oknach dialogowych](../windows/controls-in-dialog-boxes.md)