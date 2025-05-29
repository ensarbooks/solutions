# Create json for below

# Create documention

# Structure

DetailedProduct = {
id: string
title: string
description: string
subtitle?: string
category: string
slug: string
client: string
industry: string
services: string[]
challengeSummary: string
challenges: {
title: string
description: string
}[]
solutionSummary: string
solutions: {
title: string
description: string
}[]
results: string[]
documentation?: {
title?: string
path: string // Direct URL to the documentation
}
}

Solution = {
id: string
title: string
shortDescription: string
longDescription: string
slug: string
category?: string
benefits: string[]
features: {
title: string
description: string
}[]
useCases: {
title: string
description: string
}[]
documentation?: {
title?: string
path: string // Direct URL to the documentation
}
}
