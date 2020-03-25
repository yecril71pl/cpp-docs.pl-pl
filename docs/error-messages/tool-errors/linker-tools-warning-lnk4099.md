---
title: Ostrzeżenie LNK4099 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4099
helpviewer_keywords:
- LNK4099
ms.assetid: 358170a4-07cd-43fe-918f-82c32757ffc5
ms.openlocfilehash: b1f330924b8e47e0649268142106a050c83cb20a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183322"
---
# <a name="linker-tools-warning-lnk4099"></a>Ostrzeżenie LNK4099 narzędzi konsolidatora

Nie znaleziono pliku PDB "filename" z elementem "Object/Library" lub "Path"; Łączenie obiektu bez informacji debugowania

Konsolidator nie może odnaleźć pliku. pdb. Skopiuj go do katalogu, który zawiera `object/library`.

Aby znaleźć nazwę pliku. pdb skojarzonego z plikiem obiektu:

1. Wyodrębnij plik obiektu z biblioteki z biblioteką [lib](../../build/reference/lib-reference.md) **/Extract:** `objectname` **. obj** `xyz` **. lib**.

1. Sprawdź ścieżkę do pliku. pdb z **polecenia DUMPBIN/Section:. Debug $ T/rawdata** `objectname` **. obj**.

Można również kompilować z [/Z7](../../build/reference/z7-zi-zi-debug-information-format.md), aby nie trzeba było używać PDB, lub usunąć opcję [/Debug](../../build/reference/debug-generate-debug-info.md) konsolidatora, jeśli nie ma plików. pdb dla obiektów, które tworzysz.
