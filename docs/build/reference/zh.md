---
title: /ZH (algorytm wyznaczania wartości skrótu do obliczania sumy kontrolnej plików w informacjach o debugowaniu)
description: Użyj opcji kompilatora/ZH, aby włączyć sumy kontrolne pliku źródłowego MD5, SHA-1 lub SHA-256 w informacjach debugowania
ms.date: 09/16/2019
f1_keywords:
- /ZH
- /ZH:MD5
- /ZH:SHA1
- /ZH:SHA_256
helpviewer_keywords:
- /ZH
- /ZH:MD5
- /ZH:SHA1
- /ZH:SHA_256
- /ZH compiler option
- /ZH:MD5 compiler option
- /ZH:SHA1 compiler option
- /ZH:SHA_256 compiler option
- Hash algorithm for file checksum in debug info
ms.openlocfilehash: f05dc2bc3b8ce4502ff16a6e19fdbb10763b34ba
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2019
ms.locfileid: "71686874"
---
# <a name="zh-hash-algorithm-for-calculation-of-file-checksum-in-debug-info"></a>/ZH (algorytm wyznaczania wartości skrótu do obliczania sumy kontrolnej plików w informacjach o debugowaniu)

Określa, który algorytm wyznaczania wartości skrótu ma być używany do generowania sum kontrolnych każdego pliku źródłowego.

## <a name="syntax"></a>Składnia

> **/Zh:** {**MD5**|**SHA1**|**SHA_256**}

## <a name="arguments"></a>Argumenty

**/Zh: MD5**\
Użyj skrótu MD5 dla sumy kontrolnej. Ta opcja jest domyślna.

**/Zh: SHA1**\
Użyj skrótu SHA-1 dla sumy kontrolnej.

**/Zh: SHA_256**\
Użyj skrótu SHA-256 dla sumy kontrolnej.

## <a name="remarks"></a>Uwagi

Pliki PDB przechowują sumę kontrolną dla każdego pliku źródłowego skompilowanego w kodzie obiektu w skojarzonym pliku wykonywalnym. Suma kontrolna zezwala debugerowi na sprawdzenie, czy kod źródłowy, który ładuje, jest zgodny z plikiem wykonywalnym. Kompilator i debuger obsługują algorytmy wyznaczania wartości MD5, SHA-1 i SHA-256. Domyślnie kompilator używa skrótu MD5 do generowania sumy kontrolnej. Tę opcję można określić jawnie przy użyciu opcji **/zh: MD5** .

Ze względu na ryzyko kolizji w algorytmach MD5 i SHA-1 Firma Microsoft zaleca użycie opcji **/zh: SHA_256** . Skrót SHA-256 może skutkować małym wzrostem czasu kompilacji.

W przypadku określenia więcej niż jednej opcji **/zh** Ostatnia opcja jest używana.

Opcja **/zh** jest dostępna od wersji 16,4 programu Visual Studio 2019.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Ustaw listę rozwijaną **konfiguracji** na **wszystkie konfiguracje**.

1. Wybierz **Właściwości konfiguracji** > **CC++/**  >  strony właściwości**wiersza polecenia** .

1. Zmodyfikuj właściwość **Opcje dodatkowe** , aby dodać opcję **/zh: MD5**, **/zh: SHA1**lub **/zh: SHA_256** , a następnie wybierz **przycisk OK**.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora](compiler-options.md)\
[Serwer źródłowy](/windows/win32/debug/source-server-and-source-indexing)
