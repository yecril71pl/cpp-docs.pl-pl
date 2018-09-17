---
title: Narzędzia kompilacji C/C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- c.build
dev_langs:
- C++
helpviewer_keywords:
- builds [C++], C/C++ tools
- tools [C++], build
ms.assetid: 48d9daf4-6bbf-473a-8ce2-bf2923b69f80
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1a6a223e092e7ad31dd263142d2a87712eaf556b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726040"
---
# <a name="cc-build-tools"></a>Narzędzia kompilacji C/C++

Visual C++ zapewnia następujące narzędzia wiersza polecenia do wyświetlania lub modyfikowania dane wyjściowe kompilacji:

- [BSCMAKE. Plik EXE](../../build/reference/bscmake-reference.md) kompilacji pliku informacyjnego przeglądarki (.bsc), który zawiera informacje dotyczące symboli (klasy, funkcje, dane, makr i typy) w programie. Możesz wyświetlić te informacje w oknach przeglądania w środowisku deweloperskim. (Plik .bsc może być także kompilowane w środowisku programistycznym).

- [LIB. Plik EXE](../../build/reference/lib-reference.md) służy do tworzenia i zarządzania nimi Biblioteka plików obiektów Common Object File Format (COFF). Jego można również utworzyć pliki eksportu i Importuj biblioteki do definicji odwołanie, eksportowane.

- [EDITBIN. Plik EXE](../../build/reference/editbin-reference.md) jest używane do modyfikowania COFF, pliki binarne.

- [DUMPBIN. Plik EXE](../../build/reference/dumpbin-reference.md) Wyświetla informacje COFF, pliki binarne (na przykład tabela symboli).

- [NMAKE](../../build/nmake-reference.md) odczytuje i wykonuje pliki reguł programu make.

- [Errlook —](../../build/reference/value-edit-control.md), narzędzia wyszukiwania błędów, pobiera komunikat o błędzie systemu lub komunikat o błędzie modułu na podstawie wartości wprowadzone.

## <a name="see-also"></a>Zobacz też

[Dokumentacja kompilacji w języku C/C++](../../build/reference/c-cpp-building-reference.md)<br/>
[Nazwy ozdobione](../../build/reference/decorated-names.md)<br/>
[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)