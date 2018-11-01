---
title: Składnia nazwy pliku CL
ms.date: 11/04/2016
f1_keywords:
- cl
helpviewer_keywords:
- syntax, compiler filename
- paths, CL compiler filename syntax
- cl.exe compiler, filename syntax
- extensions, specifying to compiler
- file names [C++], CL compiler
- file names [C++]
ms.assetid: 3ca72586-75be-4477-b323-a1be232e80d4
ms.openlocfilehash: 929096ed169a33e0876c3afb68f3594757d61e4e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438938"
---
# <a name="cl-filename-syntax"></a>Składnia nazwy pliku CL

CL akceptuje plików o nazwach, które postępuj zgodnie z konwencją nazewnictwa plików FAT, HPFS lub systemu plików NTFS. Nazwy pliku może zawierać ścieżki pełnej lub częściowej. Pełna ścieżka zawiera nazwę dysku i co najmniej jedną nazwę katalogu. CL akceptuje nazw plików rozdzielonych przez ukośniki odwrotne (\\) lub kreski ułamkowe (/). Nazwy plików zawierające spacje muszą być ujęte w znaki podwójnego cudzysłowu. Ścieżka częściowa pomija nazwy dysku, która CL zakłada się na bieżącym dysku. Jeśli nie określisz ścieżki, CL przyjęto założenie, że plik znajduje się w bieżącym katalogu.

Rozszerzenie nazwy pliku Określa, jak są przetwarzane pliki. Pliki C i C++, które mają rozszerzenie .c, .cxx lub .cpp, są kompilowane. Inne pliki, w tym pliki .obj, biblioteki (.lib) i pliki definicji modułu (.def) są przekazywane do konsolidatora bez przetwarzany.

## <a name="see-also"></a>Zobacz też

[Składnia wiersza polecenia kompilatora](../../build/reference/compiler-command-line-syntax.md)