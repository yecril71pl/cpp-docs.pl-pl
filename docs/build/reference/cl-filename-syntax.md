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
ms.openlocfilehash: b20f88e69c6e0d1774f1cd81b3ee833c4f0ff696
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57811774"
---
# <a name="cl-filename-syntax"></a>Składnia nazwy pliku CL

CL akceptuje plików o nazwach, które postępuj zgodnie z konwencją nazewnictwa plików FAT, HPFS lub systemu plików NTFS. Nazwy pliku może zawierać ścieżki pełnej lub częściowej. Pełna ścieżka zawiera nazwę dysku i co najmniej jedną nazwę katalogu. CL akceptuje nazw plików rozdzielonych przez ukośniki odwrotne (\\) lub kreski ułamkowe (/). Nazwy plików zawierające spacje muszą być ujęte w znaki podwójnego cudzysłowu. Ścieżka częściowa pomija nazwy dysku, która CL zakłada się na bieżącym dysku. Jeśli nie określisz ścieżki, CL przyjęto założenie, że plik znajduje się w bieżącym katalogu.

Rozszerzenie nazwy pliku Określa, jak są przetwarzane pliki. Pliki C i C++, które mają rozszerzenie .c, .cxx lub .cpp, są kompilowane. Inne pliki, w tym pliki .obj, biblioteki (.lib) i pliki definicji modułu (.def) są przekazywane do konsolidatora bez przetwarzany.

## <a name="see-also"></a>Zobacz także

[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
