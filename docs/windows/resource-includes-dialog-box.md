---
title: Zasób zawiera okno dialogowe (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.resourceincludes
helpviewer_keywords:
- Resource Includes dialog box [C++]
- rc files [C++], changing storage
- symbol header files [C++], changing
- .rc files [C++], changing storage
- symbol header files [C++], read-only
- symbols [C++], symbol header files
ms.assetid: 659a54e6-e416-4045-8411-798730ff4ce3
ms.openlocfilehash: b0e7125e07deb965055da54126eb0933e64c0429
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50625069"
---
# <a name="resource-includes-dialog-box-c"></a>Zasób zawiera okno dialogowe (C++)

Możesz użyć **zasób zawiera** okno dialogowe w projekcie C++, aby zmodyfikować środowisko normalnej pracy rozmieszczenie przechowywania wszystkich zasobów w pliku .rc projektu, a wszystkie [symbole](../windows/symbols-resource-identifiers.md) w Resource.h.

Aby otworzyć **zasób zawiera** okno dialogowe, kliknij prawym przyciskiem myszy .rc w pliku [widok zasobów](../windows/resource-view-window.md), następnie wybierz **zasób zawiera** z menu skrótów.

- **Plik nagłówkowy symboli**

   Umożliwia zmianę nazwy pliku nagłówkowego, w którym przechowywane są definicje symboli dla Twojego pliku zasobu. Aby uzyskać więcej informacji, zobacz [zmiana nazwy pliki nagłówkowe symboli](../windows/changing-the-names-of-symbol-header-files.md).

- **Dyrektywy symboli tylko do odczytu**

   Można dołączyć plików nagłówkowych, które zawierają symbole, które nie powinny być modyfikowane podczas sesji. Na przykład można uwzględnić plik symboli, która jest współużytkowana przez wiele projektów. Może również obejmować pliki .h MFC. Aby uzyskać więcej informacji, zobacz [tym udostępnionych (tylko do odczytu) lub symbole obliczane](../windows/including-shared-read-only-or-calculated-symbols.md).

- **Dyrektywy czasu kompilacji**

   Pozwala dołączyć pliki zasobów, które są tworzone oraz edytowane oddzielnie z zasobów w głównego pliku zasobów, zawierać dyrektywy czasu kompilacji (takich jak te, które zostaną umieszczone zasoby warunkowo) lub zasobów w niestandardowym formacie. Można również użyć **pole dyrektywy czasu kompilacji** obejmujący standardowe pliki zasobów biblioteki MFC. Aby uzyskać więcej informacji, zobacz [tym zasobów w czasie kompilowania](../windows/how-to-include-resources-at-compile-time.md).

> [!NOTE]
> Wpisy w tych polach tekstowych pojawiają się w pliku .rc, oznaczony za `TEXTINCLUDE 1`, `TEXTINCLUDE 2`, i `TEXTINCLUDE 3` odpowiednio. Aby uzyskać więcej informacji, zobacz [TN035: przy użyciu wielu plików zasobów i plików nagłówkowych przy użyciu języka Visual C++](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md).

Po wprowadzeniu zmian do pliku zasobów za pomocą **zasób zawiera** okno dialogowe, należy zamknąć plik .rc i ponownie je, aby zmiany zaczęły obowiązywać. Aby uzyskać więcej informacji, zobacz [tym zasobów w czasie kompilowania](../windows/how-to-include-resources-at-compile-time.md).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Instrukcje: określanie katalogów dołączenia dla zasobów](../windows/how-to-specify-include-directories-for-resources.md)<br/>
[Symbole: identyfikatory zasobów](../windows/symbols-resource-identifiers.md)<br/>
[Pliki zasobów](../windows/resource-files-visual-studio.md)<br/>
[Edytory zasobów](../windows/resource-editors.md)