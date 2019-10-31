---
title: /NOPDB
description: Opcja/NOPDB zachowuje polecenia DUMPBIN ładowania i wyszukiwania plików PDB w celu uzyskania informacji o symbolach.
ms.date: 10/29/2019
f1_keywords:
- /NOPDB
helpviewer_keywords:
- /NOPDB dumpbin option
- /NOPDB
ms.openlocfilehash: 3b745049517888d13de245d4e29be3985c122ada
ms.sourcegitcommit: 6ed1bc5b26dc60a780c1fc5f2f19d57ba1dc47d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73145736"
---
# <a name="nopdb"></a>/NOPDB

Informuje polecenia DUMPBIN o konieczności załadowania i przeszukiwania plików bazy danych (PDB) programu w celu uzyskania informacji o symbolach.

## <a name="syntax"></a>Składnia

> **/NOPDB**

## <a name="remarks"></a>Uwagi

Domyślnie polecenia DUMPBIN próbuje załadować pliki PDB dla swoich docelowych plików obiektów, bibliotek lub pliku wykonywalnego. POLECENIA DUMPBIN używa tych informacji, aby dopasować adresy do nazw symboli. Proces ten może być czasochłonny, jeśli pliki PDB są duże lub muszą zostać załadowane z serwera zdalnego. Opcja **/NOPDB** informuje polecenia DUMPBIN o tym, aby pominąć ten krok. Drukuje tylko informacje o adresach i symbolach dostępne w pliku obiektu, bibliotece lub pliku wykonywalnym.

### <a name="to-set-the-nopdb-linker-option-in-visual-studio"></a>Aby ustawić opcję konsolidatora/NOPDB w programie Visual Studio

1. Otwórz okno dialogowe **strony właściwości** dla projektu. Aby uzyskać więcej informacji, [Zobacz C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz opcję **Właściwości konfiguracji** > **konsolidator** > strony właściwości **wiersza polecenia** .

1. W polu **dodatkowe opcje** Dodaj opcję **/NOPDB** . Wybierz **przycisk OK** lub **Zastosuj** , aby zapisać zmiany.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Ta opcja nie ma programowego odpowiednika.

## <a name="see-also"></a>Zobacz także

\ [wiersza polecenia polecenia DUMPBIN](dumpbin-command-line.md)
[Polecenia DUMPBIN opcje](dumpbin-options.md)\
[Odwołanie polecenia DUMPBIN](dumpbin-reference.md)
