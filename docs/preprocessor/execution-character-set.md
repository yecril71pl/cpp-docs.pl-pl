---
title: execution_character_set, pragma
ms.date: 08/29/2019
f1_keywords:
- execution_character_set
- vc-pragma.execution_character_set
helpviewer_keywords:
- pragma execution_character_set
ms.assetid: 32248cbc-7c92-4dca-8442-230c052b53ad
ms.openlocfilehash: 0c2c812f27634f397af91eace7a41c0e71c1eb99
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218622"
---
# <a name="execution_character_set-pragma"></a>execution_character_set, pragma

Określa zestaw znaków wykonywania używany dla literałów ciągów i znaków. Ta dyrektywa nie jest wymagana w przypadku literałów oznaczonych `u8` prefiksem.

## <a name="syntax"></a>Składnia

> **#pragma execution_character_set (** "*Target*" **)**

### <a name="parameters"></a>Parametry

*obiektów*\
Określa docelowy zestaw znaków wykonania. Obecnie jedynym obsługiwanym docelowym zestawem wykonywania jest "UTF-8".

## <a name="remarks"></a>Uwagi

Ta dyrektywa kompilatora jest przestarzała począwszy od programu Visual Studio 2015 Update 2. Zalecamy używanie `/execution-charset:utf-8` opcjikompilatora`/utf-8` i razem z użyciem prefiksuwprzypadkuwąskichznakówiliterałówciągówzawierającychznakirozszerzone.`u8` Aby uzyskać więcej informacji na `u8` temat prefiksu, zobacz [literały ciągów i znaków](../cpp/string-and-character-literals-cpp.md). Aby uzyskać więcej informacji na temat opcji kompilatora, zobacz [/Execution-charset (Ustawianie zestawu znaków wykonywania)](../build/reference/execution-charset-set-execution-character-set.md) i [/UTF-8 (Ustawianie zestawu znaków źródłowych i wykonywalnych na UTF-8)](../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md).

`#pragma execution_character_set("utf-8")` Dyrektywa informuje kompilator, aby zakodować wąski znak i wąski literały ciągu w kodzie źródłowym jako UTF-8 w pliku wykonywalnym. To kodowanie danych wyjściowych jest niezależne od użytego kodowania pliku źródłowego.

Domyślnie kompilator koduje wąskie znaki i wąskie ciągi przy użyciu bieżącej strony kodowej jako zestawu znaków wykonania. Oznacza to, że znaki Unicode lub DBCS w literale, które znajdują się poza zakresem bieżącej strony kodowej, są konwertowane na domyślny znak zastępczy w danych wyjściowych. Znaki Unicode i DBCS są obcinane do ich niskiej kolejności bajtów. Prawie nie jest to planowane. Można określić kodowanie UTF-8 dla literałów w pliku źródłowym przy użyciu `u8` prefiksu. Kompilator przekazuje te ciągi zakodowane UTF-8 do danych wyjściowych bez zmian. Wąskie literały znakowe poprzedzone przez użycie U8 muszą pasować do jednego bajtu lub są obcinane w danych wyjściowych.

Domyślnie program Visual Studio używa bieżącej strony kodowej jako zestawu znaków źródłowych służącego do interpretowania kodu źródłowego dla danych wyjściowych. Gdy plik jest odczytywany w programie, program Visual Studio interpretuje go zgodnie z bieżącą stroną kodową, chyba że strona kodowa została ustawiona, lub jeśli na początku pliku wykryjesz znak kolejności bajtów (BOM) lub UTF-16. Ponieważ nie można ustawić kodowania UTF-8 jako bieżącej strony kodowej, gdy automatyczne wykrywanie napotyka pliki źródłowe kodowane jako UTF-8 bez BOM, program Visual Studio zakłada, że są one kodowane przy użyciu bieżącej strony kodowej. Znaki w pliku źródłowym, które znajdują się poza zakresem określonej lub automatycznie wykrytej strony kodowej, mogą spowodować ostrzeżenia i błędy kompilatora.

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i \_ \_słowo kluczowe pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[/Execution-charset (Ustaw zestaw znaków wykonywania)](../build/reference/execution-charset-set-execution-character-set.md)\
[/utf-8 (Ustaw źródłowy i wykonywalny zestaw znaków na UTF-8)](../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)
