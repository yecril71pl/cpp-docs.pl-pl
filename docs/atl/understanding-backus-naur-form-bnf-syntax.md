---
title: Składnia rejestratora ATL i Naura formularz (BNF)
ms.date: 05/14/2019
helpviewer_keywords:
- BNF notation
- Backus-Naur form (BNF) syntax
ms.assetid: 994bbef0-9077-4aa8-bdfe-b7e830af9acc
ms.openlocfilehash: 0f07a39863b586d524d060dc3df7117e2c930b3e
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168712"
---
# <a name="understanding-backus-naur-form-bnf-syntax"></a>Opis składni notacji Backusa-Naura (BNF)

Skrypty używane przez rejestrator ATL są opisane w tym temacie przy użyciu składni BNF, która korzysta z notacji pokazanej w poniższej tabeli.

|Konwencja/symbol|Znaczenie|
|------------------------|-------------|
|::=|Odpowiednik|
|&#124;|LUB|
|X +|Jeden lub więcej XS.|
|\[Y|Symbol X jest opcjonalny. Opcjonalne ograniczniki są oznaczane przez \[].|
|Dowolny **pogrubiony** tekst|Literał ciągu.|
|Dowolny tekst *pisany kursywą*|Sposób konstruowania literału ciągu.|

Jak wskazano w powyższej tabeli, skrypty rejestratora używają literałów ciągów. Te wartości są rzeczywistym tekstem, który musi pojawić się w skrypcie. W poniższej tabeli opisano literały ciągów używane w skrypcie rejestratora ATL.

|Literał ciągu|Akcja|
|--------------------|------------|
|**ForceRemove**|Całkowicie usuwa następny klucz (jeśli istnieje), a następnie ponownie go tworzy.|
|**NoRemove**|Nie usuwa następnego klucza podczas wyrejestrowywania.|
|**użyte**|Określa, `<Key Name>` że jest to nazwana wartość.|
|**Usuwanie**|Usuwa następny klucz podczas rejestrowania.|
|**wolumin**|Określa, że następna wartość jest ciągiem (REG_SZ).|
|**Wykres**|Określa, że następna wartość jest typu DWORD (REG_DWORD).|
|**mol**|Określa, że następna wartość jest wielociągu (REG_MULTI_SZ).|
|**b**|Określa, że następna wartość jest wartością binarną (REG_BINARY).|

## <a name="bnf-syntax-examples"></a>Przykłady składni BNF

Poniżej przedstawiono kilka przykładów składni, które ułatwią zrozumienie, jak Notacja i literały ciągu działają w skrypcie rejestratora ATL.

### <a name="syntax-example-1"></a>Przykład składni 1

> \<wyrażenie rejestru>:: = \<dodaj klucz>

Określa, `registry expression` że jest równoważne `Add Key`.

### <a name="syntax-example-2"></a>Przykład składni 2

> \<wyrażenie rejestru>:: = \<dodaj klucz> | \<Usuń klucz>

Określa, `registry expression` że jest równoważne albo `Add Key` lub `Delete Key`.

### <a name="syntax-example-3"></a>Przykład składni 3

> \<Nazwa klucza>:: = "\<alfanumeryczne>+"

Określa, `Key Name` że jest równa co najmniej `AlphaNumeric` jednej wartości.

### <a name="syntax-example-4"></a>Przykład składni 4

> \<Dodaj klucz>:: = [**ForceRemove** | **NoRemove** | **Val**]\<nazwa klucza>

Określa, `Add Key` że jest równoważne `Key Name`z, i że literały ciągu, `ForceRemove`, `NoRemove`, i `val`, są opcjonalne.

### <a name="syntax-example-5"></a>Przykład składni 5

> \<> alfanumeryczne:: = *dowolny znak, który nie ma wartości null, czyli ASCII 0*

Określa, `AlphaNumeric` że jest równoznaczny z dowolnym znakiem innym niż null.

### <a name="syntax-example-6"></a>Przykład składni 6

```rgs
val 'testmulti' = m 'String 1\0String 2\0'
```

Określa, że nazwa `testmulti` klucza jest wartością wielociągową składającą `String 1` się `String 2`z i.

### <a name="syntax-example-7"></a>Przykład składni 7

```rgs
val 'testhex' = d '&H55'
```

Określa, że nazwa `testhex` klucza jest wartością DWORD ustawioną na szesnastkowe 55 (dziesiętne 85). Należy pamiętać, że ten format jest zgodny z notacją **&H** , jak znaleziono w specyfikacji Visual Basic.

## <a name="see-also"></a>Zobacz także

[Tworzenie skryptów rejestratora](../atl/creating-registrar-scripts.md)
