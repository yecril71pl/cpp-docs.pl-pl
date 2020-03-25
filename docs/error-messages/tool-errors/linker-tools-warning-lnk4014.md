---
title: Ostrzeżenie LNK4014 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4014
helpviewer_keywords:
- LNK4014
ms.assetid: 394903e9-3ded-4ea4-b7c0-a3535d4b4da4
ms.openlocfilehash: 5de53abc2342e3ed743f6b4abb871e05606dfc37
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194281"
---
# <a name="linker-tools-warning-lnk4014"></a>Ostrzeżenie LNK4014 narzędzi konsolidatora

nie można znaleźć obiektu składowego "ObjectName"

Biblioteka LIB nie może odnaleźć `objectname` w bibliotece.

Opcje **/Remove** i **/Extract** wymagają pełnej nazwy obiektu elementu członkowskiego, który ma zostać usunięty lub skopiowany do pliku. Pełna nazwa zawiera ścieżkę oryginalnego pliku obiektu. Aby wyświetlić pełne nazwy obiektów Członkowskich w bibliotece, użyj polecenia DUMPBIN [/ARCHIVEMEMBERS](../../build/reference/archivemembers.md) lub lib [/list](../../build/reference/managing-a-library.md).
