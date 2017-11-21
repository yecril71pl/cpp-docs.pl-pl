---
title: "Obsługa wolnych wątków w dostawcy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB providers, multithreaded
- threading [C++], providers
ms.assetid: a91270dc-cdf9-4855-88e7-88a54be7cbe8
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7d062a17fd71d53451aa8de3aa7d498f8a5ec68a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="supporting-free-threading-in-your-provider"></a>Obsługa wolnych wątków w dostawcy
Wszystkie klasy dostawcy OLE DB są wątkowo i wpisy rejestru są ustawione w związku z tym. Jest dobrym pomysłem jest obsługa wolnych wątków, aby zapewnić wysoką wydajność w sytuacji, w wielu użytkowników. Aby zapewnić dostawcy wątkowo, należy sprawdzić, czy kod jest prawidłowo zablokowany. Zawsze, gdy zapisu lub przechowywania danych, należy zablokować dostęp z sekcji krytycznych.  
  
 Każdy obiekt szablonu dostawcy OLE DB ma osobny rozdział krytyczne. Aby łatwiej blokuje, każda nowa klasa tworzenia powinna być biorąc klasy nadrzędnej klasy szablonu nazwa jako argument.  
  
 Poniższy przykład przedstawia sposób zablokować kodu:  
  
```  
template <class T>  
class CMyObject<T> : public...  
  
HRESULT MyObject::MyMethod(void)  
{  
   T* pT = (T*)this;      // this gets the parent class   
  
// You don't need to do anything if you are only reading information  
  
// If you want to write information, do the following:  
   pT->Lock();         // engages critical section in the object  
   ...;                // write whatever information you wish  
   pT->Unlock();       // disengages the critical section  
}  
```  
  
 Aby uzyskać więcej informacji dotyczących sposobu ochrony sekcje krytyczne z `Lock` i `Unlock`, zobacz [Multithreading: jak używać klas synchronizacji](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
 Należy także sprawdzić, czy żadnych metod można zastąpić (takie jak `Execute`) są wątkowo.  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z szablonami dostawców OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)