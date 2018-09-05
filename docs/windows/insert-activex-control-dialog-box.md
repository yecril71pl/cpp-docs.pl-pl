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
ms.openlocfilehash: ef8f2142f00b862ff198df9c75e142dc66a049b5
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43689967"
---
# <a name="insert-activex-control-dialog-box"></a>Wstawianie kontrolki ActiveX — Okno dialogowe

To okno dialogowe umożliwia [wstawić formanty ActiveX do dialogowym](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md) podczas korzystania z [Edytor okien dialogowych](../windows/dialog-editor.md).

### <a name="activex-control"></a>Kontrolki ActiveX

Wyświetla listę formantów ActiveX. Wstawianie kontrolki z tego okna dialogowego nie generuje klasę otoki. Klasa otoki, należy użyć [Widok klas](/visualstudio/ide/viewing-the-structure-of-code) ją utworzyć (Aby uzyskać więcej informacji, zobacz [Dodawanie klasy](../ide/adding-a-class-visual-cpp.md)). Jeśli formant ActiveX nie ma w tym oknie dialogowym, spróbuj zainstalować kontroli zgodnie z instrukcjami dostawcy.

### <a name="path"></a>Ścieżka

Wyświetla plik, w którym znajduje się Kontrolka ActiveX.

Możesz umieścić formantów w **przybornika** okna, aby mieć łatwy dostęp. Aby uzyskać więcej informacji, zobacz [przybornika](/visualstudio/ide/reference/).

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Karta Edytor okien dialogowych, Przybornik](../windows/dialog-editor-tab-toolbox.md)  
[Pliki zasobów](../windows/resource-files-visual-studio.md)  
[Kontrolki w oknach dialogowych](../windows/controls-in-dialog-boxes.md)