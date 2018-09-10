---
title: Tworzenie nowej niestandardowej lub zasobów danych (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.binary
dev_langs:
- C++
helpviewer_keywords:
- custom resources [C++]
- data resources [C++]
- resources [C++], creating
ms.assetid: 9918bf96-38fa-43a1-a384-572f95d84950
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6a92e7904b3b42422bebf5a80e0f1b03dd818f86
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44314587"
---
# <a name="creating-a-new-custom-or-data-resource-c"></a>Tworzenie nowej niestandardowej lub zasobów danych (C++)

Można utworzyć nowy zasób niestandardowy lub danych, umieszczając w oddzielnym pliku przy użyciu składni pliku skryptu (.rc) normalny zasób, a następnie w tym pliku zasobu, klikając prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i klikając  **Obejmuje zasobów** w menu skrótów.

### <a name="to-create-a-new-custom-or-data-resource"></a>Aby utworzyć nowy zasób niestandardowy lub danych

1. [Utwórz plik .rc](../windows/how-to-create-a-resource-script-file.md) zawierająca zasób niestandardowy lub danych.

   Niestandardowe dane można wpisać w pliku .rc, jako zakończony znakiem null cudzysłowie ciągi lub jako liczby całkowite w formacie dziesiętną, szesnastkowym lub ósemkowo.

2. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy plik .rc projektu, a następnie kliknij przycisk **zasób zawiera** w menu skrótów.

3. W **dyrektywy czasu kompilacji** wpisz `#include` instrukcję, która zawiera nazwę pliku zawierającego niestandardowego zasobu. Na przykład:

```cpp
    #include mydata.rc
 ```

   Upewnij się, że składnia i pisownię możesz wpisać są poprawne. Zawartość **dyrektywy czasu kompilacji** pola są wstawiane do pliku skryptu zasobu, dokładnie tak, jak został wpisany.

4. Kliknij przycisk **OK** zapisaniu zmian.

Innym sposobem tworzenia niestandardowego zasobu jest do zaimportowania pliku zewnętrznego jako zasób niestandardowy. Aby uzyskać więcej informacji, zobacz [importowanie i eksportowanie zasobów](../windows/how-to-import-and-export-resources.md).

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Edytor plików binarnych](binary-editor.md)