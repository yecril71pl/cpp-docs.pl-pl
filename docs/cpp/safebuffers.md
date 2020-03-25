---
title: safebuffers
ms.date: 11/04/2016
f1_keywords:
- safebuffers_cpp
helpviewer_keywords:
- __declspec keyword (C++), safebuffers
- safebuffers __declspec keyword
ms.assetid: 0b0dce14-4523-44d2-8070-5dd0fdabc618
ms.openlocfilehash: 705d3eca67f87e505a147af4984496d3af43dd53
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178915"
---
# <a name="safebuffers"></a>safebuffers

**Specyficzne dla firmy Microsoft**

Informuje kompilator, aby nie wstawiać sprawdzeń zabezpieczeń przepełnienia buforu dla funkcji.

## <a name="syntax"></a>Składnia

```
__declspec( safebuffers )
```

## <a name="remarks"></a>Uwagi

Opcja kompilatora **/GS** powoduje, że kompilator testuje przekroczenia buforu przez wstawianie kontroli zabezpieczeń na stosie. Typy struktur danych, które kwalifikują się do kontroli zabezpieczeń, są opisane w [/GS (sprawdzanie zabezpieczeń bufora)](../build/reference/gs-buffer-security-check.md). Aby uzyskać więcej informacji na temat wykrywania przepełnienia buforu, zobacz [funkcje zabezpieczeń w programie MSVC](https://blogs.msdn.microsoft.com/vcblog/2017/06/28/security-features-in-microsoft-visual-c/).

Przegląd kodu lub zewnętrzna analiza eksperta może pomóc w ustaleniu, czy funkcja jest zabezpieczona przed przepełnieniem buforu. W takim przypadku można pominąć sprawdzanie zabezpieczeń dla funkcji, stosując słowo kluczowe **__declspec (safebuffers)** do deklaracji funkcji.

> [!CAUTION]
>  Sprawdzenia zabezpieczeń buforu zapewniają istotną ochronę i mają niewielki wpływ na wydajność. Dlatego zaleca się, aby nie pomijać ich poza rzadkimi przypadkami, gdy wydajność funkcji odgrywa krytyczną rolę i wiadomo, że funkcja jest bezpieczna.

## <a name="inline-functions"></a>Funkcje śródwierszowe

*Funkcja podstawowa* może użyć słowa kluczowego nakreślania, aby wstawić kopię *funkcji pomocniczej*. [inlining](inline-functions-cpp.md) Jeśli do funkcji zostanie zastosowane słowo kluczowe **__declspec (safebuffers)** , wykrywanie przepełnienia buforu jest pomijane dla tej funkcji. Niepodkreślanie ma jednak wpływ na słowo kluczowe **__declspec (safebuffers)** w następujący sposób.

Załóżmy, że opcja kompilatora **/GS** jest określona dla obu funkcji, ale podstawowa funkcja określa słowo kluczowe **__declspec (safebuffers)** . Struktury danych w funkcji pomocniczej uprawniają ją do sprawdzania zabezpieczeń i funkcja nie pomija tych sprawdzeń. W takim przypadku:

- Określ słowo kluczowe [__forceinline](inline-functions-cpp.md) w funkcji pomocniczej, aby wymusić, aby kompilator mógł być wbudowany w funkcję bez względu na optymalizacje kompilatora.

- Ponieważ funkcja pomocnicza kwalifikuje się do sprawdzenia zabezpieczeń, sprawdzanie zabezpieczeń jest również stosowane do podstawowej funkcji, mimo że określa słowo kluczowe **__declspec (safebuffers)** .

## <a name="example"></a>Przykład

Poniższy kod ilustruje sposób używania słowa kluczowego **__declspec (safebuffers)** .

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

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[__declspec](../cpp/declspec.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[wbudowane, __inline, \__forceinline](inline-functions-cpp.md)<br/>
[strict_gs_check](../preprocessor/strict-gs-check.md)
