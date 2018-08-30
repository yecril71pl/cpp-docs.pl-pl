---
title: 'Porady: określanie katalogów dołączenia dla zasobów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- directories [C++], specifying include paths for resources
- include files, specifying for resources
- resources [Visual Studio], including in projects
ms.assetid: d6a7c0f6-4810-4bb0-b4b7-7d2476a20ca2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c52f2a17e347e7b37152a3d7a78423f0523b5679
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43220601"
---
# <a name="how-to-specify-include-directories-for-resources"></a>Porady: określanie katalogów dołączenia dla zasobów

### <a name="to-specify-include-directories-for-a-specific-rc-file"></a>W celu określenia katalogów dołączanych dla określonego pliku .rc

1. Kliknij prawym przyciskiem myszy plik .rc w Eksploratorze rozwiązań i wybierz **właściwości** z menu skrótów.

2. W **stron właściwości** okno dialogowe, kliknij przycisk **zasobów** węzła w okienku po lewej stronie, następnie określ dodatkowe katalogi dołączane we **dodatkowe katalogi dołączane** Właściwość.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w przewodniku dewelopera .NET Framework. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Instruktaż: Using Resources for Localization with ASP.NET](https://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Dołączone zasoby, okno dialogowe](../windows/resource-includes-dialog-box.md)  
[TN035: używanie wielu plików zasobów i plików nagłówków z programem Visual C++](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)  
[Symbole: identyfikatory zasobów](../windows/symbols-resource-identifiers.md)  
[Pliki zasobów](../windows/resource-files-visual-studio.md)  
[Edytory zasobów](../windows/resource-editors.md)