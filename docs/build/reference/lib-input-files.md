---
title: Pliki wyjściowe LIB
ms.date: 11/04/2016
helpviewer_keywords:
- input files, LIB
ms.assetid: e1236f0d-cd90-446b-b900-f311f456085c
ms.openlocfilehash: de81f79eecf3fc73c02894747f4b97cb107cf892
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328226"
---
# <a name="lib-input-files"></a>Pliki wyjściowe LIB

Pliki wejściowe oczekiwane przez LIB zależą od trybu, w którym jest używany, jak pokazano w poniższej tabeli.

|Tryb|Dane wejściowe|
|----------|-----------|
|Domyślnie (tworzenie lub modyfikowanie biblioteki)|Pliki obiektów COFF (obj), biblioteki COFF (lib), pliki obiektów 32-bitowego formatu modelu obiektów (OMF) (obj)|
|Wyodrębnianie elementu członkowskiego za pomocą /EXTRACT|Biblioteka COFF (.lib)|
|Tworzenie pliku eksportu i importowanie biblioteki za pomocą /DEF|Plik module-definition (.def), pliki obiektów COFF (obj), biblioteki COFF (lib), 32-bitowe pliki obiektów OMF (obj)|

> [!NOTE]
> Biblioteki OMF utworzone przez 16-bitową wersję LIB nie mogą być używane jako dane wejściowe do 32-bitowej wersji LIB.

## <a name="see-also"></a>Zobacz też

[Informacje o LIB](overview-of-lib.md)
