---
title: "leaderboard"
description: "leaderboard for task 2"
menu: task2
draft: false
weight: 80
---

---

{{< chart >}}
{
    type: 'bar',
    data: {
        labels: ['Baseline'],
        datasets: [{
            label: 'Results for task 2: Regression',
            data: [0.13578],
            backgroundColor: [
                'rgba(255, 99, 132, 0.2)'
            ],
            borderColor: [
                'rgba(255, 99, 132, 1)'
            ],
            borderWidth: 1
        }]
    },
    options: {
        maintainAspectRatio: false,
        scales: {
            yAxes: [{
                ticks: {
                    beginAtZero: true
                }
            }]
        }
    }
}
{{< /chart >}}
