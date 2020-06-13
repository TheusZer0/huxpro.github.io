---
layout: post
title: "pregunta temporal"
subtitle: 'TryHackMe - Hacktivities - First ReverseEngineering'
date: 2020-05-25 12:00:00
author: "TheusZero"
header-img: "images/post/Reverse/portada.png"
catalog: true
comments: true
tags:
  - Programacion
  - Linux
  - Machine
  - Explotations
  - Upgrade
  - Shell
  - Root
  - User
  - Reverse Engineering
---

```Python
char * encrypt(char* str){
    int i,j,poly[MAXCHAR],x,k;
    i=0;
    while(str[i]!='\0')
    {
        if((str[i]>=0&&str[i]<=31)||(str[i]>=33&&str[i]<65)||(str[i]>90&&str[i]<97)||(str[i]>122&&str[i]<=127))
        {
            NULL;
        }
        i++;
    }
    x=0;
    k=11;
    //Assigning Polybius Square numbers to alphabets
    for(i=0;i<=25;i++)
    {
        if(i<=8)
        {
            if(i%5==0&&i!=0)
            {
                k+=5;
                poly[x]=k++;
            }
            else{
                poly[x]=k++;
            }
        }
        if(i>=10)
        {
            if(i%5==0&&i!=0)
            {
                poly[x]=k++;
                k+=5;
            }
            else{
                poly[x]=k++;
            }
        }
        if(i==9)
        {
            poly[x]=24;
        }
        x++;
    }
    i=0;
//    printf("Encrypted Code using Polybius Square Cipher \n");
    while(str[i]!='\0')
    {
        if(!((str[i]>=0&&str[i]<=31)||(str[i]>=33&&str[i]<65)||(str[i]>90&&str[i]<97)||(str[i]>122&&str[i]<=127)))
        {
            if(str[i]>='A'&&str[i]<='Z')
            {
                printf("%d",poly[str[i]-'A']);
            }
            if(str[i]>='a'&&str[i]<='z')
            {
                printf("%d",poly[str[i]-'a']);
            }
        }
        if(str[i]==' ')
        {
            printf("%c",str[i]);
        }
        i++;
    }
    printf("\n");
}
```


