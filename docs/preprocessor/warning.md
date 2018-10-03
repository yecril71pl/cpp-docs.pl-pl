---
title: Ostrzeżenie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- warning_CPP
- vc-pragma.warning
dev_langs:
- C++
helpviewer_keywords:
- pragmas, warning
- push pragma warning
- pop warning pragma
- warning pragma
ms.assetid: 8e9a0dec-e223-4657-b21d-5417ebe29cc8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 90cb11a6e6ab0c088c0b2425856d61556e76564c
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2018
ms.locfileid: "48234635"
---
# <a name="warning-pragma"></a>Ostrzeżenie Pragma
Umożliwia selektywne modyfikacji zachowania wiadomości ostrzeżeń kompilatora.

## <a name="syntax"></a>Składnia

```
#pragma warning(
    warning-specifier : warning-number-list [; warning-specifier : warning-number-list...] )
#pragma warning( push[ ,n ] )
#pragma warning( pop )
```

## <a name="remarks"></a>Uwagi

Dostępne są następujące parametry specyfikator ostrzeżenie.

|Ostrzeżenie — Specyfikator|Znaczenie|
|------------------------|-------------|
|*1, 2, 3, 4*|Zastosowanie danego poziomu do określonego ostrzeżenia. Włącza to również określone ostrzeżenie, która jest domyślnie wyłączona.|
|*default*|Resetuj zachowanie ostrzeżenie do wartości domyślnej. Włącza to również określone ostrzeżenie, która jest domyślnie wyłączona. Ostrzeżenie będzie generowane w lokalizacji domyślnej, udokumentowane, poziom.<br /><br /> Aby uzyskać więcej informacji, zobacz [kompilatora ostrzeżenia, są wyłączone domyślnie](../preprocessor/compiler-warnings-that-are-off-by-default.md).|
|*Wyłącz*|Generuje określony komunikaty ostrzegawcze.|
|*Błąd*|Należy sporządzić raport określone ostrzeżenia jako błędy.|
|*once*|Wyświetl komunikaty określony tylko jeden raz.|
|*Pomiń*|Wypycha bieżący stan pragmy w stosie, wyłącza określone ostrzeżenie następnego wiersza, a tak, aby stan pragmy jest resetowany punktów POP stosu ostrzeżenie.|

Poniższa instrukcja kodu pokazuje, że `warning-number-list` parametru może zawierać wiele numerów ostrzeżeń, a wiele `warning-specifier` parametry można określić w tym samym dyrektywa pragmy.

```cpp
#pragma warning( disable : 4507 34; once : 4385; error : 164 )
```

To jest funkcjonalnie równoważny z następującym kodem.

```cpp
// Disable warning messages 4507 and 4034.
#pragma warning( disable : 4507 34 )

// Issue warning 4385 only once.
#pragma warning( once : 4385 )

// Report warning 4164 as an error.
#pragma warning( error : 164 )
```

Kompilator sam doda 4000 na dowolną liczbę ostrzeżenia, który jest od 0 do 999.

Dla numerów ostrzeżeń w zakresie 4700-4999, które są skojarzone z generowania kodu, stan ostrzeżenia obowiązuje w przypadku, gdy kompilator napotka otwartych nawiasów klamrowych funkcji będzie obowiązywać przez pozostałą część tej funkcji. Za pomocą **ostrzeżenie** pragmy w funkcji, które można zmienić stanu ostrzeżenie, że ma wiele większa niż 4699 zostanie aktywowane dopiero po zakończeniu wykonywania funkcji. Poniższy przykład pokazuje poprawne położenie **ostrzeżenie** pragm, aby wyłączyć ostrzeżenia generowania kodu, a następnie przywrócić go.

```cpp
// pragma_warning.cpp
// compile with: /W1
#pragma warning(disable:4700)
void Test() {
   int x;
   int y = x;   // no C4700 here
   #pragma warning(default:4700)   // C4700 enabled after Test ends
}

int main() {
   int x;
   int y = x;   // C4700
}
```

Należy zauważyć, że w całej funkcji treści ostatnie ustawienie **ostrzeżenie** pragma będą obowiązywać dla całej funkcji.

## <a name="push-and-pop"></a>Wypychanie i Pop

**Ostrzeżenie** pragma obsługuje również następującej składni, gdzie *n* reprezentuje poziom ostrzeżenia (od 1 do 4).

`#pragma warning( push [ , n ] )`

`#pragma warning( pop )`

Pragmy `warning( push )` zapisuje bieżący stan ostrzegawczy każde ostrzeżenie. Pragmy `warning( push, n )` zapisuje bieżący stan każde ostrzeżenie i ustawia poziom ostrzeżeń globalnego *n*.

Pragmy `warning( pop )` POP ostatni stan ostrzeżenia są wypychane na stosie. Wszelkie zmiany wprowadzone w stan ostrzegawczy między *wypychania* i *pop* zostaną cofnięte. Rozważmy następujący przykład:

```cpp
#pragma warning( push )
#pragma warning( disable : 4705 )
#pragma warning( disable : 4706 )
#pragma warning( disable : 4707 )
// Some code
#pragma warning( pop )
```

Na końcu niniejszego Kodeksu *pop* przywraca stan każde ostrzeżenie (w tym 4705 4706 i 4707) jakie były na początku kodu.

Podczas zapisywania plików nagłówkowych, możesz użyć *wypychania* i *pop* celu zagwarantowania, czy zmiany stanu ostrzeżenia wprowadzone przez użytkownika uniemożliwia nagłówki kompilowanie poprawnie. Użyj *wypychania* na początku tego nagłówka i *pop* na końcu. Na przykład w przypadku nagłówka, który nie kompiluje się prawidłowo na poziom ostrzeżeń 4 poniższy kod może zmienić poziom ostrzeżeń 3 i następnie przywrócić oryginalny poziom ostrzeżeń na końcu nagłówka.

```cpp
#pragma warning( push, 3 )
// Declarations/definitions
#pragma warning( pop )
```

Aby uzyskać więcej informacji na temat kompilatora pominąć opcje, które ułatwiają ostrzeżenia, zobacz [/FI](../build/reference/fi-name-forced-include-file.md) i [Wn](../build/reference/compiler-option-warning-level.md).

## <a name="see-also"></a>Zobacz też

[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)