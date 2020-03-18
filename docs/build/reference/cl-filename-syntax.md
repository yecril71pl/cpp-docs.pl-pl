---
title: Składnia nazwy pliku CL
ms.date: 11/04/2016
helpviewer_keywords:
- syntax, compiler filename
- paths, CL compiler filename syntax
- cl.exe compiler, filename syntax
- extensions, specifying to compiler
- file names [C++], CL compiler
- file names [C++]
ms.assetid: 3ca72586-75be-4477-b323-a1be232e80d4
ms.openlocfilehash: 1135e5c682b79fec5de808b61c93d370f05a3aa9
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440238"
---
# <a name="cl-filename-syntax"></a>Składnia nazwy pliku CL

CL akceptuje pliki o nazwach zgodnych z konwencjami nazewnictwa FAT, HPFS lub NTFS. Każda nazwa pliku może zawierać pełną lub częściową ścieżkę. Pełna ścieżka zawiera nazwę dysku i jedną lub więcej nazw katalogów. CL akceptuje nazwy plików rozdzielone ukośnikami (\\) lub ukośnikami (/). Nazwy plików zawierające spacje muszą być ujęte w znaki podwójnego cudzysłowu. Ścieżka częściowa pomija nazwę dysku, który CL przyjmuje jako bieżący dysk. Jeśli ścieżka nie zostanie określona, CL przyjmie, że plik znajduje się w bieżącym katalogu.

Rozszerzenie nazwy pliku określa sposób przetwarzania plików. Pliki c C++ i, które mają rozszerzenie. c,. cxx lub. cpp, są kompilowane. Inne pliki, w tym pliki obj, biblioteki (. lib) i pliki definicji modułów (. def), są przesyłane do konsolidatora bez przetwarzania.

## <a name="see-also"></a>Zobacz też

[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
