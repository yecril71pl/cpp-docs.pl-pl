---
title: Ostrzeżenie LNK4070 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4070
helpviewer_keywords:
- LNK4070
ms.assetid: f95f179a-fff9-427e-bd51-466b3934517f
ms.openlocfilehash: 391a477625b51fd37eacc5d455801ce90d2abbc2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194008"
---
# <a name="linker-tools-warning-lnk4070"></a>Ostrzeżenie LNK4070 narzędzi konsolidatora

/OUT: filename — dyrektywa w. Różnica jest inna niż nazwa pliku wyjściowego "filename"; ignorowanie dyrektywy

`filename` określony w instrukcji [name](../../build/reference/name-c-cpp.md) lub [Library](../../build/reference/library.md) , gdy plik EXP został utworzony różni się od `filename` wyjściowego, który został przyjęty domyślnie lub określony przy użyciu opcji [/out](../../build/reference/out-output-file-name.md) .

To ostrzeżenie zostanie wyświetlone, jeśli zmienisz nazwę pliku wyjściowego w środowisku deweloperskim, a plik. def projektu nie został zaktualizowany. Ręcznie zaktualizuj plik. def, aby rozwiązać to ostrzeżenie.

Program kliencki, który używa uzyskanej biblioteki DLL, może napotkać problemy.
