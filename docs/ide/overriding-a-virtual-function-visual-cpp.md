---
title: Zastępują funkcję wirtualną
ms.date: 11/12/2018
f1_keywords:
- vc.codewiz.virtualfunc.override
helpviewer_keywords:
- virtual functions, overriding
- base classes, overriding virtual functions defined in
- Properties window, overriding virtual functions in
ms.assetid: 2d8c76f2-7a6b-4c9c-8de5-4282ce7755b6
ms.openlocfilehash: 9bb3fd34bbfa14cce1595ed586c4e1b66518e7b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62350559"
---
# <a name="override-a-virtual-function"></a>Zastępują funkcję wirtualną

Możesz przesłonić funkcji wirtualnych zdefiniowanych w klasie bazowej programu Visual Studio [okno właściwości](/visualstudio/ide/reference/properties-window).

**Aby przesłonić funkcji wirtualnej w oknie dialogowym właściwości:**

1. W widoku klas wybierz klasę.

1. W oknie dialogowym właściwości wybierz **zastępuje** przycisku.

   > [!NOTE]
   > **Zastępuje** przycisk jest dostępny po wybraniu nazwy klasy w widoku klas lub po wybraniu w oknie źródła.

   Kolumna po lewej stronie zawiera funkcje wirtualne. Jeśli nazwa funkcji wirtualnej pojawi się również w prawej kolumnie, zastąpienie już została zaimplementowana.

1. Jeśli żadne przesłonięcie funkcji, a następnie wybierz komórkę w prawej kolumnie w oknie dialogowym właściwości, aby wyświetlić sugerowane nazwę funkcji zastąpienia jako \<Dodaj >*FuncName*.

1. Wybierz sugerowanej nazwy, aby dodać kodu klasy zastępczej dla funkcji.

1. Aby edytować funkcji przez nadrzędne, kliknij dwukrotnie nazwę funkcji w widoku klas i edytowanie kodu w oknie źródła.

Aby usunąć zastąpienia, wybierz nazwę funkcji zastąpienie w prawej kolumnie, a następnie wybierz \<Usuń >*FuncName*. Kod funkcji jest opatrzona komentarzem.
