---
title: Składnia nazwy pliku CL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- cl
dev_langs:
- C++
helpviewer_keywords:
- syntax, compiler filename
- paths, CL compiler filename syntax
- cl.exe compiler, filename syntax
- extensions, specifying to compiler
- file names [C++], CL compiler
- file names [C++]
ms.assetid: 3ca72586-75be-4477-b323-a1be232e80d4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 04d82be73f2e73a24daeabd6219abdeadcb4cbbf
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716888"
---
# <a name="cl-filename-syntax"></a>Składnia nazwy pliku CL

CL akceptuje plików o nazwach, które postępuj zgodnie z konwencją nazewnictwa plików FAT, HPFS lub systemu plików NTFS. Nazwy pliku może zawierać ścieżki pełnej lub częściowej. Pełna ścieżka zawiera nazwę dysku i co najmniej jedną nazwę katalogu. CL akceptuje nazw plików rozdzielonych przez ukośniki odwrotne (\\) lub kreski ułamkowe (/). Nazwy plików zawierające spacje muszą być ujęte w znaki podwójnego cudzysłowu. Ścieżka częściowa pomija nazwy dysku, która CL zakłada się na bieżącym dysku. Jeśli nie określisz ścieżki, CL przyjęto założenie, że plik znajduje się w bieżącym katalogu.

Rozszerzenie nazwy pliku Określa, jak są przetwarzane pliki. Pliki C i C++, które mają rozszerzenie .c, .cxx lub .cpp, są kompilowane. Inne pliki, w tym pliki .obj, biblioteki (.lib) i pliki definicji modułu (.def) są przekazywane do konsolidatora bez przetwarzany.

## <a name="see-also"></a>Zobacz też

[Składnia wiersza polecenia kompilatora](../../build/reference/compiler-command-line-syntax.md)