---
title: strict_gs_check | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- strict_gs_check
- strict_gs_check_CPP
dev_langs: C++
helpviewer_keywords: strict_gs_check pragma
ms.assetid: decfec81-c916-42e0-a07f-8cc26df6a7ce
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5c355bd385a997e8ff3fd9ec323d50bb33b9c6fd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="strictgscheck"></a>strict_gs_check
Tej pragmy udostępnia zwiększone zabezpieczenia sprawdzania.  
  
## <a name="syntax"></a>Składnia  
  
```  
#pragma strict_gs_check([push,] on )   
#pragma strict_gs_check([push,] off )   
#pragma strict_gs_check(pop)  
```  
  
## <a name="remarks"></a>Uwagi  
 Instruuje kompilator, aby wstawić osiągnięciem losowego pliku cookie w stosie funkcja pomaga wykrywać niektórych kategorii przepełnienie buforu opartego na stosie. Domyślnie /GS (Sprawdzanie zabezpieczeń bufora) — opcja kompilatora nie wstawia plik cookie dla wszystkich funkcji. Aby uzyskać więcej informacji, zobacz [/GS (Sprawdzanie zabezpieczeń bufora)](../build/reference/gs-buffer-security-check.md).  
  
 Należy skompilować z/GS (buforu sprawdzanie zabezpieczeń) umożliwiające strict_gs_check.  
  
 Użyj tej pragmy w modułów kodu, które są widoczne dla potencjalnie niebezpiecznych danych. Tej pragmy bardzo agresywnie i zastosowano je do funkcji, które nie może być konieczne tej ochrony, ale jest zoptymalizowana, aby zminimalizować jego wpływ na wydajność aplikacji wynikowy.  
  
 Nawet jeśli używasz tej pragmy powinien starań, aby zapisać bezpieczny kod. Oznacza to upewnij się, że kod ma nie przepełnienia buforu. strict_gs_check może chronić aplikacji z przepełnienia buforu, które pozostają w kodzie.  
  
## <a name="example"></a>Przykład  
 W poniższym kodzie przepełnienie buforu występuje, gdy firma Microsoft kopiowania tablicy do lokalnej tablicy. Podczas kompilowania tego kodu z/GS pliki cookie nie jest wstawiany stosu, ponieważ typem danych tablicy jest wskaźnik. Dodawanie strict_gs_check pragma wymusza cookie stosu w stosie funkcji.  
  
```cpp  
// pragma_strict_gs_check.cpp  
// compile with: /c  
  
#pragma strict_gs_check(on)  
  
void ** ReverseArray(void **pData,  
                     size_t cData)  
{  
    // *** This buffer is subject to being overrun!! ***  
    void *pReversed[20];  
  
    // Reverse the array into a temporary buffer  
    for (size_t j = 0, i = cData; i ; --i, ++j)  
        // *** Possible buffer overrun!! ***  
            pReversed[j] = pData[i];   
  
    // Copy temporary buffer back into input/output buffer  
    for (size_t i = 0; i < cData ; ++i)   
        pData[i] = pReversed[i];  
  
    return pData;  
}  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
 [/GS (Sprawdzanie zabezpieczeń bufora)](../build/reference/gs-buffer-security-check.md)