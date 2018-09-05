---
title: 'Porady: Kopiowanie zasobów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.resvw.resource.copying
- vs.resvw.resource.copying
dev_langs:
- C++
helpviewer_keywords:
- resources [Visual Studio], moving between files
- resources [Visual Studio], copying
- resource files, copying or moving resources between
- resource files, tiling
- .rc files, copying resources between
- rc files, copying resources between
ms.assetid: 65f523e8-017f-4fc6-82d1-083c56d9131f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 20abc194f1286e47477c4510f9ceef6250b9b3f7
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43687222"
---
# <a name="how-to-copy-resources"></a>Porady: zasoby dotyczące kopiowania

Możesz skopiować zasoby z jednego pliku do innego bez ich zmieniania lub możesz [zmiana języka lub warunku zasobu podczas kopiowania go](../windows/how-to-change-the-language-or-condition-of-a-resource-while-copying.md).

Można go łatwo skopiować zasoby z istniejącego zasobu lub plik wykonywalny do bieżącego pliku zasobów. Aby to zrobić, należy otworzyć oba pliki zawierające zasoby w tym samym czasie i przeciągnij elementy z jednego pliku lub skopiuj i Wklej między dwoma plikami. Ta metoda działa w przypadku plików skryptu (.rc) zasobów i plików szablonów (.rct) zasobu, a także pliki wykonywalne (.exe).

> [!NOTE]
> Visual C++ zawiera przykładowe pliki zasobów, które można użyć w swojej aplikacji. Aby uzyskać więcej informacji, zobacz [CLIPART: wspólnych zasobów](https://github.com/Microsoft/VCSamples).

Metodą przeciągania i upuszczania między plikami .rc, które są otwarte [poza projektem](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

### <a name="to-copy-resources-between-files-using-the-drag-and-drop-method"></a>Aby umożliwić kopiowanie zasobów między plikami przy użyciu metody przeciągania i upuszczania

1. Otwórz zarówno autonomiczne pliki zasobów (Aby uzyskać więcej informacji, zobacz [wyświetlanie zasobów .rc z zewnętrznego pliku projektu](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)). Na przykład otworzyć Source1.rc i Source2.rc.

2. W pierwszym pliku .rc kliknij zasób, który chcesz skopiować. Na przykład w `Source1.rc`, kliknij przycisk **IDD_DIALOG1**.

3. Naciśnij i przytrzymaj klawisz CTRL i przeciągnij go do drugiego pliku .rc. Na przykład przeciągać **IDD_DIALOG1** z `Source1.rc` do `Source2.rc`.

   > [!NOTE]
   > Przeciąganie zasób bez przytrzymywania **Ctrl** klucz przenosi zasobu, a nie skopiować go.

### <a name="to-copy-resources-using-copy-and-paste"></a>Do kopiowania zasobów za pomocą kopiowania i wklejania

1. Otwórz zarówno autonomiczne pliki zasobów (Aby uzyskać więcej informacji, zobacz [wyświetlanie zasobów .rc z zewnętrznego pliku projektu](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)). Na przykład Source1.rc i Source2.rc.

2. W pliku źródłowym, z którego chcesz skopiować zasobu (na przykład `Source1.rc`), kliknij prawym przyciskiem myszy zasób i wybierz polecenie **kopiowania** z menu skrótów.

3. Kliknij prawym przyciskiem myszy plik zasobów, do którego chcesz wkleić zasobu (na przykład `Source2.rc`). Wybierz **Wklej** z menu skrótów.

   > [!NOTE]
   > Użytkownik nie przeciągnij i upuść, kopiowanie, wycinanie lub wklejanie danych między plikami zasobów w projekcie (**widok zasobów**) i pliki .rc autonomicznej, (te otwarte w oknach dokumentów). Można to zrobić w poprzednich wersjach produktu.

   > [!NOTE]
   > Aby uniknąć konfliktów z nazwami symboli lub wartości z istniejącego pliku, Visual C++ może ulec zmianie wartości symboli zasobu przeniesionych lub nazwy symbolu i wartości po skopiuj go do nowego pliku.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Instrukcje: otwieranie pliku skryptu zasobu spoza projektu (autonomicznego)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)  
[Pliki zasobów](../windows/resource-files-visual-studio.md)  
[Edytory zasobów](../windows/resource-editors.md)