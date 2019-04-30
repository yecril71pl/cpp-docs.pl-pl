---
title: Ostrzeżenie LNK4070 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4070
helpviewer_keywords:
- LNK4070
ms.assetid: f95f179a-fff9-427e-bd51-466b3934517f
ms.openlocfilehash: e7139b21f053ea8633356c7194cd719a6a4aef35
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410268"
---
# <a name="linker-tools-warning-lnk4070"></a>Ostrzeżenie LNK4070 narzędzi konsolidatora

/ Out: nazwa_pliku dyrektywy w. EXP różni się od nazwy pliku wyjściowego 'NazwaPliku'; dyrektywa została zignorowana

`filename` Określonych w [nazwa](../../build/reference/name-c-cpp.md) lub [biblioteki](../../build/reference/library.md) instrukcji podczas tworzenia pliku .exp różni się od danych wyjściowych `filename` , był domyślnie zakłada, że albo określony za pomocą [/OUT](../../build/reference/out-output-file-name.md) opcji.

Jeśli zmienisz nazwę pliku wyjściowego w środowisku deweloperskim i gdzie plik .def projektu nie zostało zaktualizowane, zostanie wyświetlone to ostrzeżenie. Ręcznie zaktualizować plik .def, aby rozwiązać tego ostrzeżenia.

Program kliencki, który używa wynikowej biblioteki DLL mogą wystąpić problemy.