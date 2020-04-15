---
title: safebuffers
ms.date: 11/04/2016
f1_keywords:
- safebuffers_cpp
helpviewer_keywords:
- __declspec keyword (C++), safebuffers
- safebuffers __declspec keyword
ms.assetid: 0b0dce14-4523-44d2-8070-5dd0fdabc618
ms.openlocfilehash: bc4736ce233ce026ecab9ef38ac8379466b5a0bc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365584"
---
# <a name="safebuffers"></a>safebuffers

**Specyficzne dla firmy Microsoft**

Informuje kompilator, aby nie wstawiać sprawdzeń zabezpieczeń przepełnienia buforu dla funkcji.

## <a name="syntax"></a>Składnia

```
__declspec( safebuffers )
```

## <a name="remarks"></a>Uwagi

Opcja kompilatora **/GS** powoduje, że kompilator testuje przepełnienie buforu przez wstawienie kontroli zabezpieczeń na stosie. Typy struktur danych, które kwalifikują się do kontroli zabezpieczeń są opisane w [/GS (Kontrola zabezpieczeń bufora)](../build/reference/gs-buffer-security-check.md). Aby uzyskać więcej informacji na temat wykrywania przepełnienia buforu, zobacz [Funkcje zabezpieczeń w ustroju MSVC](https://blogs.msdn.microsoft.com/vcblog/2017/06/28/security-features-in-microsoft-visual-c/).

Przegląd kodu lub zewnętrzna analiza eksperta może pomóc w ustaleniu, czy funkcja jest zabezpieczona przed przepełnieniem buforu. W takim przypadku można pominąć kontrole zabezpieczeń dla funkcji, stosując słowo kluczowe **__declspec(safebuffers)** do deklaracji funkcji.

> [!CAUTION]
> Sprawdzenia zabezpieczeń buforu zapewniają istotną ochronę i mają niewielki wpływ na wydajność. Dlatego zaleca się, aby nie pomijać ich poza rzadkimi przypadkami, gdy wydajność funkcji odgrywa krytyczną rolę i wiadomo, że funkcja jest bezpieczna.

## <a name="inline-functions"></a>Funkcje śródwierszowe

*Funkcja podstawowa* może użyć słowa kluczowego [inlining,](inline-functions-cpp.md) aby wstawić kopię *funkcji pomocniczej*. Jeśli słowo kluczowe **__declspec(safebuffers)** jest stosowane do funkcji, wykrywanie przepełnienia buforu jest pomijane dla tej funkcji. Jednak inline wpływa na **__declspec (safebuffers)** słowo kluczowe w następujący sposób.

Załóżmy, że opcja **kompilatora /GS** jest określona dla obu funkcji, ale funkcja podstawowa określa **słowo kluczowe __declspec(safebuffers).** Struktury danych w funkcji pomocniczej uprawniają ją do sprawdzania zabezpieczeń i funkcja nie pomija tych sprawdzeń. W takim przypadku:

- Określ [__forceinline](inline-functions-cpp.md) słowo kluczowe w funkcji pomocniczej, aby wymusić kompilator do wbudowanej tej funkcji, niezależnie od optymalizacji kompilatora.

- Ponieważ funkcja pomocnicza kwalifikuje się do kontroli zabezpieczeń, kontrole zabezpieczeń są również stosowane do funkcji podstawowej, nawet jeśli określa **słowo kluczowe __declspec (safebuffers).**

## <a name="example"></a>Przykład

Poniższy kod pokazuje, jak używać słowa kluczowego **__declspec(safebuffers).**

```cpp
// compile with: /c /GS
typedef struct {
    int x[20];
} BUFFER;
static int checkBuffers() {
    BUFFER cb;
    // Use the buffer...
    return 0;
};
static __declspec(safebuffers)
    int noCheckBuffers() {
    BUFFER ncb;
    // Use the buffer...
    return 0;
}
int wmain() {
    checkBuffers();
    noCheckBuffers();
    return 0;
}
```

**ZAKOŃCZ Specyficzne dla firmy Microsoft**

## <a name="see-also"></a>Zobacz też

[__declspec](../cpp/declspec.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[w linii, __inline, \__forceinline](inline-functions-cpp.md)<br/>
[strict_gs_check](../preprocessor/strict-gs-check.md)
