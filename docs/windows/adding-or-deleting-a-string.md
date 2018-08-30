---
title: Dodawanie lub usuwanie ciągu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.string
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], adding to string tables
- string tables, deleting strings
- strings [C++], deleting in string tables
- string tables, adding strings
ms.assetid: 077077b4-0f4b-4633-92d6-60b321164cab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 952531a846fe48e9f093f016efd67d73c386d82c
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43204490"
---
# <a name="adding-or-deleting-a-string"></a>Dodawanie lub usuwanie ciągu

Można szybko wstawić nowych wpisów do tabeli ciągów przy użyciu **ciąg** edytora. Nowych ciągów są umieszczane na końcu tabeli i podano następny dostępny identyfikator. Następnie można edytować **identyfikator**, **wartość**, lub **podpis** właściwości w [okno właściwości](/visualstudio/ide/reference/properties-window) zgodnie z potrzebami.

**Ciąg** edytora upewnia się, nie należy używać Identyfikatora, który jest już używana. Wybranie Identyfikatora już w użyciu **ciąg** edytora zostanie powiadamiania o, a następnie przypisz ogólny Unikatowy identyfikator, na przykład `IDS_STRING58113`.

### <a name="to-add-a-string-table-entry"></a>Aby dodać wpis tabeli ciągów

1. Otwórz tabeli ciągów, klikając dwukrotnie odpowiednią ikonę w [widok zasobów](../windows/resource-view-window.md).

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

2. Kliknij prawym przyciskiem myszy w tabeli ciągów, a następnie wybierz **nowy ciąg** z menu skrótów.

3. W **ciąg** edytora, wybierz opcję **identyfikator** z listy rozwijanej identyfikator lub wpisz identyfikator bezpośrednio od razu.

4. Edytuj **wartość**, jeśli to konieczne.

5. Wpisz wpis dla **podpis**.

   > [!NOTE]
   > Ciągów o wartości null są niedozwolone w tabelach ciągów Windows. Jeśli tworzysz wpis w tabeli ciągów, który jest pusty ciąg, zostanie wyświetlony komunikat z prośbą do "Wprowadź ciąg dla tego wpisu w tabeli."

### <a name="to-delete-a-string-table-entry"></a>Aby usunąć wpis tabeli ciągów

1. Wybierz wpis, który chcesz usunąć.

2. Na **Edytuj** menu, kliknij przycisk **Usuń**.

\- lub —

- Kliknij prawym przyciskiem myszy ciągu chcesz usunąć, a następnie wybierz **Usuń** z menu skrótów.

\- lub —

- Naciśnij klawisz **Usuń** klucza.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, (te, których platformą docelową środowiska uruchomieniowego języka wspólnego), zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Instruktaż: Lokalizowanie interfejsów Windows Forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3\(v=vs.100\)).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Edytor ciągów](../windows/string-editor.md)  