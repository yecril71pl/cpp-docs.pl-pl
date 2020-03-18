---
title: Kolejność opcji CL (C++) — Visual Studio
ms.date: 12/14/2018
helpviewer_keywords:
- cl.exe compiler, setting options
ms.assetid: 300908ce-ae00-4b45-964b-e4e69ff6777b
ms.openlocfilehash: 6c57a68dd15d82a9d6a01bfe145374bda6eb1510
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439199"
---
# <a name="order-of-cl-options"></a>Kolejność opcji CL

Opcje mogą znajdować się w dowolnym miejscu w wierszu polecenia CL, z wyjątkiem opcji/link, która musi wystąpić jako Ostatnia. Kompilator rozpoczyna się od opcji określonych w [zmiennej środowiskowej CL](cl-environment-variables.md) , a następnie odczytuje wiersz polecenia od lewej do prawej — pliki poleceń przetwarzania w kolejności, w jakiej napotkają. Każda opcja ma zastosowanie do wszystkich plików w wierszu polecenia. Jeśli CL napotykają opcje powodujące konflikt, użyje prawej opcji.

## <a name="see-also"></a>Zobacz też

[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
