---
title: "Obsługa wolnych wątków w dostawcy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, multithreaded
- threading [C++], providers
ms.assetid: a91270dc-cdf9-4855-88e7-88a54be7cbe8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5cd5ce6b852b490334cbc8d49c6e967efffb3a6e
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
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