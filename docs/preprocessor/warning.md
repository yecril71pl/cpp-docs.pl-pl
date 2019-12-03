---
title: warning — Wartość dyrektywy pragma
ms.date: 08/29/2019
f1_keywords:
- warning_CPP
- vc-pragma.warning
helpviewer_keywords:
- pragmas, warning
- push pragma warning
- pop warning pragma
- warning pragma
ms.assetid: 8e9a0dec-e223-4657-b21d-5417ebe29cc8
ms.openlocfilehash: c6c9668f614f932b0a96f30ad3e0395e39ddc400
ms.sourcegitcommit: d0504e2337bb671e78ec6dd1c7b05d89e7adf6a7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2019
ms.locfileid: "74683345"
---
# <a name="warning-pragma"></a>warning — Wartość dyrektywy pragma

Włącza wybiórczą modyfikację zachowania komunikatów ostrzeżeń kompilatora.

## <a name="syntax"></a>Składnia

> **ostrzeżenie #pragma (** \
> &nbsp;&nbsp;&nbsp;&nbsp;*ostrzegawczy specyfikator* **:** *Warning-Number-list*\
> &nbsp;&nbsp;&nbsp;&nbsp;[ **;** *ostrzegawczy specyfikator* **:** *Warning-Number-list* ...] **)** \
> **Ostrzeżenie #pragma (wypychanie** [ **,** *n* ] **)** \
> **Ostrzeżenie #pragma (pop)**

## <a name="remarks"></a>Uwagi

Dostępne są następujące parametry specyfikatora ostrzegawczego.

|Ostrzeżenie — specyfikator|Znaczenie|
|------------------------|-------------|
|*1, 2, 3, 4*|Zastosuj podany poziom do określonych ostrzeżeń. Ponadto włącza również określone ostrzeżenie, które jest domyślnie wyłączone.|
|*default*|Zresetuj zachowanie ostrzeżenia do wartości domyślnej. Ponadto włącza również określone ostrzeżenie, które jest domyślnie wyłączone. Ostrzeżenie zostanie wygenerowane na jego domyślnym, udokumentowanym poziomie.<br /><br /> Aby uzyskać więcej informacji, zobacz [ostrzeżenia kompilatora, które są domyślnie wyłączone](../preprocessor/compiler-warnings-that-are-off-by-default.md).|
|*wyłącza*|Nie wystawiaj określonych komunikatów ostrzegawczych.|
|*Porn*|Zgłoś określone ostrzeżenia jako błędy.|
|*once*|Wyświetlaj tylko określone komunikaty tylko raz.|
|*kół*|Wypchnij bieżący stan dyrektywy pragma na stosie, wyłącza określone Ostrzeżenie dla następnego wiersza, a następnie wyświetla stos ostrzegawczy, tak aby stan dyrektywy pragma został zresetowany.|

Poniższa instrukcja Code ilustruje, że parametr `warning-number-list` może zawierać wiele wartości ostrzegawczych, a wiele parametrów `warning-specifier` można określić w tej samej dyrektywie pragma.

```cpp
#pragma warning( disable : 4507 34; once : 4385; error : 164 )
```

Ta dyrektywa jest funkcjonalnie równoważna z poniższym kodem:

```cpp
// Disable warning messages 4507 and 4034.
#pragma warning( disable : 4507 34 )

// Issue warning 4385 only once.
#pragma warning( once : 4385 )

// Report warning 4164 as an error.
#pragma warning( error : 164 )
```

Kompilator dodaje 4000 do dowolnej liczby ostrzeżeń, która jest z zakresu od 0 do 999.

W przypadku numerów ostrzeżeń w zakresie 4700-4999, które są skojarzone z generowaniem kodu, stan ostrzeżenia obowiązuje, gdy kompilator napotka definicję funkcji będzie obowiązywać dla reszty funkcji. Użycie dyrektywy pragma **ostrzeżenia** w funkcji w celu zmiany stanu ostrzeżenia o wartości większej niż 4699 zacznie obowiązywać dopiero po zakończeniu funkcji. W poniższym przykładzie pokazano poprawne rozmieszczenie pragm **ostrzeżeń** , aby wyłączyć komunikat ostrzegawczy generowania kodu, a następnie przywrócić go.

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

Należy zauważyć, że w całej treści funkcji, ostatnie ustawienie dyrektywy pragma **Warning** będzie obowiązywać dla całej funkcji.

## <a name="push-and-pop"></a>Wypchnij i wyskakujące

Pragma **ostrzeżenia** obsługuje również następującą składnię, gdzie *n* reprezentuje poziom ostrzeżenia (od 1 do 4).

`#pragma warning( push [ , n ] )`

`#pragma warning( pop )`

Pragma `warning( push )` zapisuje bieżący stan ostrzeżenia dla każdego ostrzeżenia. Pragma `warning( push, n )` zapisuje bieżący stan dla każdego ostrzeżenia i ustawia globalny poziom ostrzeżeń na *n*.

Pragma `warning( pop )` punkty POP z ostatnim stanem ostrzeżenia wypychane na stosie. Wszystkie zmiany wprowadzone w stanie ostrzegawczym między *wypchnięciem* i *pop* są cofnięte. Rozważmy następujący przykład:

```cpp
#pragma warning( push )
#pragma warning( disable : 4705 )
#pragma warning( disable : 4706 )
#pragma warning( disable : 4707 )
// Some code
#pragma warning( pop )
```

Na końcu tego kodu, *pop* przywraca stan każdego ostrzeżenia (zawiera 4705, 4706 i 4707) do tego, co było na początku kodu.

Podczas pisania plików nagłówkowych można użyć *polecenia push* i *pop* , aby zagwarantować, że zmiany stanu ostrzegawczego wykonywane przez użytkownika nie uniemożliwiają poprawnego kompilowania nagłówków. Użyj *wypychania* na początku nagłówka i *pop* na końcu. Na przykład jeśli masz nagłówek, który nie kompiluje się na poziomie ostrzeżenia 4, poniższy kod zmienia poziom ostrzeżeń na 3, a następnie przywraca oryginalny poziom ostrzeżeń na końcu nagłówka.

```cpp
#pragma warning( push, 3 )
// Declarations/definitions
#pragma warning( pop )
```

Aby uzyskać więcej informacji na temat opcji kompilatora, które pomagają pominąć ostrzeżenia, zobacz [/Fi](../build/reference/fi-name-forced-include-file.md) i [/w](../build/reference/compiler-option-warning-level.md).

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
