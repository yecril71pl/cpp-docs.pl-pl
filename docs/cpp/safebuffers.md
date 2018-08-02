---
title: safebuffers | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- safebuffers_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword (C++), safebuffers
- safebuffers __declspec keyword
ms.assetid: 0b0dce14-4523-44d2-8070-5dd0fdabc618
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b41646dbde21f68c2cc23dfbcf977d9f5ad06c1e
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39467498"
---
# <a name="safebuffers"></a>safebuffers
**Microsoft Specific**  
  
 Informuje kompilator, aby nie wstawiać sprawdzeń zabezpieczeń przepełnienia buforu dla funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
__declspec( safebuffers )  
```  
  
## <a name="remarks"></a>Uwagi  
 **/GS** — opcja kompilatora powoduje, że kompilator testuje przepełnienia buforu, wstawiając sprawdzenia zabezpieczeń na stosie. Rodzaje struktur danych, które są uprawnione do sprawdzania zabezpieczeń opisano w [/GS (Sprawdzanie zabezpieczeń bufora)](../build/reference/gs-buffer-security-check.md). Aby uzyskać więcej informacji dotyczących wykrywania przepełnienia buforu, zobacz [sprawdzania zabezpieczeń w kompilatorze](http://go.microsoft.com/fwlink/p/?linkid=7260) w witrynie MSDN w sieci Web.  
  
 Przegląd kodu lub zewnętrzna analiza eksperta może pomóc w ustaleniu, czy funkcja jest zabezpieczona przed przepełnieniem buforu. W takim przypadku można pominąć sprawdzanie zabezpieczeń dla funkcji, stosując **__declspec(safebuffers)** — słowo kluczowe do deklaracji funkcji.  
  
> [!CAUTION]
>  Sprawdzenia zabezpieczeń buforu zapewniają istotną ochronę i mają niewielki wpływ na wydajność. Dlatego zaleca się, aby nie pomijać ich poza rzadkimi przypadkami, gdy wydajność funkcji odgrywa krytyczną rolę i wiadomo, że funkcja jest bezpieczna.  
  
## <a name="inline-functions"></a>Funkcje śródwierszowe  
 A *podstawowa funkcja* służy [inlining](inline-functions-cpp.md) — słowo kluczowe, aby wstawić kopię *funkcji pomocniczej*. Jeśli **__declspec(safebuffers)** — słowo kluczowe jest stosowany do funkcji, Detekcja przepełnienia buforu jest pomijana dla tej funkcji. Jednakże wbudowanie wpływa na **__declspec(safebuffers)** — słowo kluczowe w następujący sposób.  
  
 Załóżmy, że **/GS** — opcja kompilatora jest określona dla obu funkcji, ale podstawowa funkcja określa **__declspec(safebuffers)** — słowo kluczowe. Struktury danych w funkcji pomocniczej uprawniają ją do sprawdzania zabezpieczeń i funkcja nie pomija tych sprawdzeń. W takim przypadku:  
  
-   Określ [__forceinline](inline-functions-cpp.md) — słowo kluczowe dla funkcji pomocniczej w celu wymuszenia aby kompilator wbudował tę funkcję niezależnie od optymalizacji kompilatora.  
  
-   Ponieważ funkcja pomocnicza jest uprawniona do sprawdzenia zabezpieczeń, kontroli zabezpieczeń są również stosowane do funkcji podstawowej, nawet, jeśli Określa on **__declspec(safebuffers)** — słowo kluczowe.  
  
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
 [__declspec](../cpp/declspec.md)   
 [Keywords](../cpp/keywords-cpp.md)   
 [w tekście, __inline, \__forceinline](inline-functions-cpp.md)   
 [strict_gs_check](../preprocessor/strict-gs-check.md)