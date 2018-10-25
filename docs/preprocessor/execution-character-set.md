---
title: execution_character_set | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- execution_character_set
- vc-pragma.execution_character_set
dev_langs:
- C++
helpviewer_keywords:
- pragma execution_character_set
ms.assetid: 32248cbc-7c92-4dca-8442-230c052b53ad
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b81832ba31fc8ef36510ce4f35c9fb1a5f3426b9
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50075024"
---
# <a name="executioncharacterset"></a>execution_character_set

Określa zestaw znaków wykonania, które są używane w literałach ciągów i znakowe. Ta dyrektywa nie jest wymagana dla literałów oznaczone z prefiksem u8.

## <a name="syntax"></a>Składnia

```
#pragma execution_character_set("target")
```

### <a name="parameters"></a>Parametry

*Docelowy*<br/>
Określa zestaw znaków wykonania docelowego. Obecnie tylko wykonanie docelowego zestawu obsługiwane jest "utf-8".

## <a name="remarks"></a>Uwagi

Ta dyrektywa kompilatora jest przestarzały, począwszy od programu Visual Studio 2015 Update 2. Firma Microsoft zaleca użycie `/execution-charset:utf-8` lub `/utf-8` opcje kompilatora wraz z przy użyciu `u8` prefiks wąskie literały znakowe i zawierających znaki specjalne. Aby uzyskać więcej informacji na temat `u8` prefiksu, zobacz [literały ciągów i znakowe](../cpp/string-and-character-literals-cpp.md). Aby uzyskać więcej informacji na temat opcji kompilatora, zobacz [/Execution-Charset (Ustaw zestaw znaków wykonywania)](../build/reference/execution-charset-set-execution-character-set.md) i [/UTF-8 (Ustaw źródłowy i wykonywalny zestawów na UTF-8 znaków)](../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md).

`#pragma execution_character_set("utf-8")` Dyrektywy informuje kompilator, aby zakodować wąskie znakowe i literały ciągu wąskiego w kodzie źródłowym jako UTF-8 w pliku wykonywalnym. Kodowanie wyjścia jest niezależna od plików źródłowych kodowanie używane.

Domyślnie kompilator koduje wąskie znaków i ciągów wąskie przy użyciu bieżącej stronie kodowej jako zestaw znaków wykonania. Oznacza to, że Unicode lub znaków Dwubajtowych znaków literału, które wykraczają poza zakres bieżącej stronie kodowej są konwertowane na domyślnym znakiem zastępującym w danych wyjściowych. Unicode i znaków Dwubajtowych znaków są zaokrąglane do ich mniej znaczący bajt. To prawie na pewno nie co planowane. Można określić kodowania UTF-8 dla literałów w pliku źródłowym, za pomocą `u8` prefiks. Kompilator przekazuje te ciągi zakodowane w formacie UTF-8 danych wyjściowych bez zmian. Literały wąskiego znaku, poprzedzony przy użyciu u8 muszą mieścić się w jednym bajtem lub są one obcięte w danych wyjściowych.

Domyślnie program Visual Studio używa bieżącej stronie kodowej jako źródłowy zestaw znaków używany do interpretacji parametrów kodu źródłowego dla danych wyjściowych. Podczas odczytywania pliku w Visual Studio interpretuje słowa kluczowe go zgodnie z bieżącej stronie kodowej, chyba, że została ustawiona na stronę kodową pliku lub znacznik kolejności bajtów (BOM) lub UTF-16 znaków, które są wykrywane na początku pliku. UTF-8 nie może być ustawione jako bieżącej stronie kodowej, gdy automatyczne wykrywanie napotka pliki źródłowe zakodowanymi w formacie UTF-8 bez BOM, dlatego Visual Studio zakłada, że zostaną one zakodowane przy użyciu bieżącej stronie kodowej. Znaki w pliku źródłowym, które są spoza zakresu określonego lub automatycznie wykrył, że strona kodowa może spowodować ostrzeżenia kompilatora i błędów.

## <a name="see-also"></a>Zobacz też

[Dyrektywy pragma i \_ \_Pragma — słowo kluczowe](../preprocessor/pragma-directives-and-the-pragma-keyword.md)<br/>
[/ Execution-Charset (Ustaw zestaw znaków wykonywania)](../build/reference/execution-charset-set-execution-character-set.md)<br/>
[/utf-8 (Ustaw źródłowy i wykonywalny zestaw znaków na UTF-8)](../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)