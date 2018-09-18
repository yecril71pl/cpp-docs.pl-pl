---
title: Ostrzeżenie LNK4070 narzędzi konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4070
dev_langs:
- C++
helpviewer_keywords:
- LNK4070
ms.assetid: f95f179a-fff9-427e-bd51-466b3934517f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9cfb4ae1c5440742c491d9615a2b4929a9b04f66
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106963"
---
# <a name="linker-tools-warning-lnk4070"></a>Ostrzeżenie LNK4070 narzędzi konsolidatora

/ Out: nazwa_pliku dyrektywy w. EXP różni się od nazwy pliku wyjściowego 'NazwaPliku'; dyrektywa została zignorowana

`filename` Określonych w [nazwa](../../build/reference/name-c-cpp.md) lub [biblioteki](../../build/reference/library.md) instrukcji podczas tworzenia pliku .exp różni się od danych wyjściowych `filename` , był domyślnie zakłada, że albo określony za pomocą [/OUT](../../build/reference/out-output-file-name.md) opcji.

Jeśli zmienisz nazwę pliku wyjściowego w środowisku deweloperskim i gdzie plik .def projektu nie zostało zaktualizowane, zostanie wyświetlone to ostrzeżenie. Ręcznie zaktualizować plik .def, aby rozwiązać tego ostrzeżenia.

Program kliencki, który używa wynikowej biblioteki DLL mogą wystąpić problemy.