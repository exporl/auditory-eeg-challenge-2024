---
title: "leaderboard"
description: "description of the test set for task 1"
menu: task1
weight: 80
---

---

{{< chart >}}
{
    type: 'bar',
    data: {
        labels: ['Baseline'],
        datasets: [{
            label: 'Results for task 1: Match-mismatch',
            data: [0.71],
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
