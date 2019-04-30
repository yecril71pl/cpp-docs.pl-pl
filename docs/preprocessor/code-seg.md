---
title: code_seg
ms.date: 11/04/2016
f1_keywords:
- code_seg_CPP
- vc-pragma.code_seg
helpviewer_keywords:
- pragmas, code_seg
- code_seg pragma
ms.assetid: bf4faac1-a511-46a6-8d9e-456851d97d56
ms.openlocfilehash: e566fb01bf70b343b75254a10466bdda2bc7ce1b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403506"
---
# <a name="codeseg"></a>code_seg
Określa segment tekstu, w którym funkcje są przechowywane w pliku .obj.

## <a name="syntax"></a>Składnia

```
#pragma code_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )
```

### <a name="parameters"></a>Parametry

**push**<br/>
(Opcjonalnie) Umieszcza rekord na wewnętrznym stosie kompilatora. A **wypychania** może mieć *identyfikator* i *nazwą segmentu*.

**POP**<br/>
(Opcjonalnie) Usuwa rekord z góry wewnętrznego stosu kompilatora.

*Identyfikator*<br/>
(Opcjonalnie) Gdy jest używane z **wypychania**, przypisuje nazwę rekordowi na wewnętrznym stosie kompilatora. Gdy jest używane z **pop**, zdejmuje rekordy z wewnętrznego stosu aż do usunięcia *identyfikator* zostanie usunięta; Jeśli *identyfikator* nie zostanie znaleziony na wewnętrznym stosie, nic nie zostanie zdjęte.

*Identyfikator* umożliwia wielu rekordów zostać zdjęte ze stosu przy użyciu tylko jednego **pop** polecenia.

"*nazwą segmentu*"<br/>
(Opcjonalnie) Nazwa segmentu. Gdy jest używane z **pop**, stos jest zdejmowany i *nazwą segmentu* staje się aktywną nazwą segmentu tekstu.

"*klasy segmentu*"<br/>
(Opcjonalnie) Ignorowanie, ale włączone dla zachowania zgodności z c++ w wersji wcześniejszej niż wersja 2.0.

## <a name="remarks"></a>Uwagi

**Code_seg** dyrektywa pragmy nie kontroluje umieszczania kodu obiektowego wygenerowanego dla szablonów skonkretyzowanych ani kodu niejawnie wygenerowanego przez kompilator — na przykład funkcji specjalnych elementów członkowskich. Firma Microsoft zaleca użycie [__declspec(code_seg(...)) ](../cpp/code-seg-declspec.md) zamiast tego atrybutu, ponieważ daje on kontrolę nad umieszczaniem całego kodu obiektowego. Obejmuje to kod wygenerowany przez kompilator.

A *segmentu* w .obj pliku to nazwany blok danych, który jest ładowany do pamięci jako jednostka. A *segment tekstu* to segment, który zawiera kod wykonywalny. W tym artykule terminy *segmentu* i *sekcji* są używane zamiennie.

**Code_seg** dyrektywa pragmy informuje kompilator, aby umieścić cały kolejny kod obiektowy z jednostki translacji w segmencie tekstu o nazwie *nazwą segmentu*. Domyślnie segment tekstu używany dla funkcji w pliku .obj ma nazwę .text.

A **code_seg** dyrektywa pragmy bez parametrów resetuje nazwę segmentu tekstu dla kolejnego kodu obiektowego do postaci .text.

Możesz użyć [DUMPBIN. Plik EXE](../build/reference/dumpbin-command-line.md) aplikacji, aby wyświetlić pliki .obj. Wersje DUMPBIN dla każdej obsługiwanej architektury docelowej są dołączone do programu Visual Studio.

## <a name="example"></a>Przykład

W tym przykładzie pokazano, jak używać **code_seg** dyrektywa pragmy do kontroli, gdy kod obiektowy jest umieszczany:

```cpp
// pragma_directive_code_seg.cpp
void func1() {                  // stored in .text
}

#pragma code_seg(".my_data1")
void func2() {                  // stored in my_data1
}

#pragma code_seg(push, r1, ".my_data2")
void func3() {                  // stored in my_data2
}

#pragma code_seg(pop, r1)      // stored in my_data1
void func4() {
}

int main() {
}
```

Aby uzyskać listę nazw, które nie powinny być używane do tworzenia sekcji, zobacz [/SECTION](../build/reference/section-specify-section-attributes.md).

Można również określić sekcje dla danych zainicjowanych ([data_seg](../preprocessor/data-seg.md)), niezainicjowanych danych ([bss_seg](../preprocessor/bss-seg.md)) i zmiennych const ([const_seg](../preprocessor/const-seg.md)).

## <a name="see-also"></a>Zobacz także

[code_seg (__declspec)](../cpp/code-seg-declspec.md)<br/>
[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)