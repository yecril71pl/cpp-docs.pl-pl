---
title: safebuffers
ms.date: 11/04/2016
f1_keywords:
- safebuffers_cpp
helpviewer_keywords:
- __declspec keyword (C++), safebuffers
- safebuffers __declspec keyword
ms.assetid: 0b0dce14-4523-44d2-8070-5dd0fdabc618
ms.openlocfilehash: 473a838a48ed6523ce78d0bc8128dd83636c81d6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62267386"
---
# <a name="safebuffers"></a>safebuffers

**Microsoft Specific**

Informuje kompilator, aby nie wstawiać sprawdzeń zabezpieczeń przepełnienia buforu dla funkcji.

## <a name="syntax"></a>Składnia

```
__declspec( safebuffers )
```

## <a name="remarks"></a>Uwagi

**/GS** — opcja kompilatora powoduje, że kompilator testuje przepełnienia buforu, wstawiając sprawdzenia zabezpieczeń na stosie. Rodzaje struktur danych, które są uprawnione do sprawdzania zabezpieczeń opisano w [/GS (Sprawdzanie zabezpieczeń bufora)](../build/reference/gs-buffer-security-check.md). Aby uzyskać więcej informacji dotyczących wykrywania przepełnienia buforu, zobacz [funkcji zabezpieczeń w MSVC](https://blogs.msdn.microsoft.com/vcblog/2017/06/28/security-features-in-microsoft-visual-c/).

Przegląd kodu lub zewnętrzna analiza eksperta może pomóc w ustaleniu, czy funkcja jest zabezpieczona przed przepełnieniem buforu. W takim przypadku można pominąć sprawdzanie zabezpieczeń dla funkcji, stosując **__declspec(safebuffers)** — słowo kluczowe do deklaracji funkcji.

> [!CAUTION]
>  Sprawdzenia zabezpieczeń buforu zapewniają istotną ochronę i mają niewielki wpływ na wydajność. Dlatego zaleca się, aby nie pomijać ich poza rzadkimi przypadkami, gdy wydajność funkcji odgrywa krytyczną rolę i wiadomo, że funkcja jest bezpieczna.

## <a name="inline-functions"></a>Funkcje śródwierszowe

A *podstawowa funkcja* służy [inlining](inline-functions-cpp.md) — słowo kluczowe, aby wstawić kopię *funkcji pomocniczej*. Jeśli **__declspec(safebuffers)** — słowo kluczowe jest stosowany do funkcji, Detekcja przepełnienia buforu jest pomijana dla tej funkcji. Jednakże wbudowanie wpływa na **__declspec(safebuffers)** — słowo kluczowe w następujący sposób.

Załóżmy, że **/GS** — opcja kompilatora jest określona dla obu funkcji, ale podstawowa funkcja określa **__declspec(safebuffers)** — słowo kluczowe. Struktury danych w funkcji pomocniczej uprawniają ją do sprawdzania zabezpieczeń i funkcja nie pomija tych sprawdzeń. W takim przypadku:

- Określ [__forceinline](inline-functions-cpp.md) — słowo kluczowe dla funkcji pomocniczej w celu wymuszenia aby kompilator wbudował tę funkcję niezależnie od optymalizacji kompilatora.

- Ponieważ funkcja pomocnicza jest uprawniona do sprawdzenia zabezpieczeń, kontroli zabezpieczeń są również stosowane do funkcji podstawowej, nawet, jeśli Określa on **__declspec(safebuffers)** — słowo kluczowe.

## <a name="example"></a>Przykład

Poniższy kod przedstawia sposób użycia **__declspec(safebuffers)** — słowo kluczowe.

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

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[__declspec](../cpp/declspec.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[w tekście, __inline, \__forceinline](inline-functions-cpp.md)<br/>
[strict_gs_check](../preprocessor/strict-gs-check.md)