---
layout: post
title: "Javascript Algorithms"
date: 2019-05-28
---

#at least one base case and one recursive case
Count from 1 - 10 using a recussion
function counter(n) {
    console.log(n);
    if (n == 10) 
        return;

    return counter(n+1);
}

counter(0);
