---
title: safebuffers | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- safebuffers_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword (C++), safebuffers
- safebuffers __declspec keyword
ms.assetid: 0b0dce14-4523-44d2-8070-5dd0fdabc618
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eb9541bfc4a94253ac26e118e22c3abb2663a893
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="safebuffers"></a>safebuffers
**Dotyczące firmy Microsoft**  
  
 Informuje kompilator, aby nie wstawiać sprawdzeń zabezpieczeń przepełnienia buforu dla funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
__declspec( safebuffers )  
```  
  
## <a name="remarks"></a>Uwagi  
 **/GS** — opcja kompilatora powoduje, że kompilator, aby przetestować nastąpiło przepełnienie buforu, wstawiając kontroli zabezpieczeń na stosie. Typy struktur danych, które kwalifikują się do kontroli zabezpieczeń są opisane w [/GS (Sprawdzanie zabezpieczeń bufora)](../build/reference/gs-buffer-security-check.md). Aby uzyskać więcej informacji na temat wykrywania przepełnienie buforu, zobacz [kompilatora zabezpieczeń sprawdza w głębokość](http://go.microsoft.com/fwlink/p/?linkid=7260) w witrynie MSDN.  
  
 Przegląd kodu lub zewnętrzna analiza eksperta może pomóc w ustaleniu, czy funkcja jest zabezpieczona przed przepełnieniem buforu. W takim przypadku można pominąć kontroli zabezpieczeń dla funkcji, stosując `__declspec(safebuffers)` — słowo kluczowe do deklaracji funkcji.  
  
> [!CAUTION]
>  Sprawdzenia zabezpieczeń buforu zapewniają istotną ochronę i mają niewielki wpływ na wydajność. Dlatego zaleca się, aby nie pomijać ich poza rzadkimi przypadkami, gdy wydajność funkcji odgrywa krytyczną rolę i wiadomo, że funkcja jest bezpieczna.  
  
## <a name="inline-functions"></a>Funkcje śródwierszowe  
 A *podstawowej funkcji* można użyć [ze śródwierszowaniem](inline-functions-cpp.md) — słowo kluczowe, aby wstawić kopię *dodatkowej funkcji*. Jeśli `__declspec(safebuffers)` — słowo kluczowe jest stosowane do funkcji, wykrywania przepełnienie buforu jest pominięta dla tej funkcji. Jednak ze śródwierszowaniem wpływa na `__declspec(safebuffers)` — słowo kluczowe w następujący sposób.  
  
 Załóżmy, że **/GS** — opcja kompilatora jest określona dla obu tych funkcji, ale określa podstawową funkcją `__declspec(safebuffers)` — słowo kluczowe. Struktury danych w funkcji pomocniczej uprawniają ją do sprawdzania zabezpieczeń i funkcja nie pomija tych sprawdzeń. W takim przypadku:  
  
-   Określ [__forceinline](inline-functions-cpp.md) — słowo kluczowe w dodatkowej funkcji, aby wymusić kompilator wbudowany, która działa niezależnie od tego, optymalizacje kompilatora.  
  
-   Ponieważ funkcja dodatkowej jest uprawniona do kontroli zabezpieczeń, kontrole zabezpieczeń również są stosowane do podstawowej funkcji, mimo że Określa `__declspec(safebuffers)` — słowo kluczowe.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób użycia `__declspec(safebuffers)` — słowo kluczowe.  
  
```  
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
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [__declspec](../cpp/declspec.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)   
 [w tekście, __inline, \__forceinline](inline-functions-cpp.md)   
 [strict_gs_check](../preprocessor/strict-gs-check.md)