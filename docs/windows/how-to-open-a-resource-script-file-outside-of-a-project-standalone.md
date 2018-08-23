---
title: 'Porady: otwieranie pliku skryptu zasobu spoza projektu (autonomicznego) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.resource
dev_langs:
- C++
helpviewer_keywords:
- resources [Visual Studio], viewing
- rc files, viewing resources
- .rc files, viewing resources
- resource script files, viewing resources
ms.assetid: bc350c60-178d-4c5d-9a7e-6576b0c936e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2711c34d55c4f4a7f1acfba4f315e06768623014
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42600913"
---
# <a name="how-to-open-a-resource-script-file-outside-of-a-project-standalone"></a>Porady: otwieranie pliku skryptu zasobu spoza projektu (autonomicznego)

Zasoby można wyświetlić w pliku .rc, bez konieczności jest otwarty projekt. Plik .rc zostanie otwarty w oknie dokumentu, w przeciwieństwie do otwarcia w [widok zasobów](../windows/resource-view-window.md) okna (co jest wykonywane, gdy plik jest otwarty w projekcie).

> [!NOTE]
> Jest to ważna różnica, ponieważ niektóre polecenia są dostępne tylko wtedy, gdy plik jest otwarty autonomiczny (spoza projektu). Na przykład, można tylko zapisywania pliku w innym formacie lub innej nazwy pliku po otwarciu pliku spoza projektu ( **Zapisz jako** polecenie jest niedostępne, gdy plik jest otwarty w projekcie).

### <a name="to-open-an-rc-file-outside-a-project"></a>Aby otworzyć plik .rc poza projektem

1. Z **pliku** menu, wybierz **Otwórz**, następnie kliknij przycisk **pliku**.

2. W **Otwórz plik** okno dialogowe, przejdź do pliku skryptu zasobu, aby wyświetlić, zaznacz plik i kliknij przycisk **Otwórz**.

   > [!NOTE]
   > Jeśli Otwórz projekt (**pliku**, **Otwórz**, **projektu**), niektóre polecenia nie będą dostępne dla Ciebie. Otwieranie pliku "autonomicznej" oznacza, otwierając go bez pierwszego ładowania projektu.

Aby otworzyć i wyświetlić plik zasobów w formacie tekstowym, zobacz [edycji skrypt zasobu (.rc) pliku](../windows/how-to-open-a-resource-script-file-in-text-format.md).

### <a name="to-open-multiple-rc-files-outside-a-project"></a>Aby otworzyć wiele plików .rc poza projektem

1. Otwórz zarówno autonomiczne pliki zasobów. Na przykład otworzyć `Source1.rc` i `Source2.rc`.

   1. Z **pliku** menu, wybierz **Otwórz**, następnie kliknij przycisk **pliku**.

   2. W **Otwórz plik** okno dialogowe, przejdź do pierwszego pliku skryptu zasobu, który chcesz otworzyć (`Source1.rc`), zaznacz plik i kliknij przycisk **Otwórz**.

   3. Powtórz poprzedni krok, aby otworzyć drugiego pliku .rc (`Source2.rc`).

       Pliki .rc są teraz otwarte w oddzielnych dokumentów w systemie windows.

2. Gdy oba pliki .rc są otwarte, Kafelek systemu windows, dzięki czemu można je wyświetlić, jednocześnie:

   - Z **okna** menu, wybierz **nową grupę karta pozioma** lub **nowej grupie pionowej karcie**.

       \- lub —

   - Kliknij prawym przyciskiem myszy jeden z plików .rc i wybierz polecenie **nową grupę karta pozioma** lub **nowej grupie pionowej karcie** z menu skrótów.

> [!NOTE]
> Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Pliki zasobów](../windows/resource-files-visual-studio.md)  
[Edytory zasobów](../windows/resource-editors.md)