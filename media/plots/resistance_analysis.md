
# Convert Temperature and Pressure to factors for ANOVA
X037..1.$Temperature_Factor <- as.factor(X037..1.$Temperature)
X037..1.$Pressure_Factor <- as.factor(X037..1.$Pressure)

# Perform ANOVA to assess the effect of Temperature and Pressure on PartResistance
aov_model <- aov(PartResistance ~ Temperature_Factor * Pressure_Factor, data = X037..1.)
summary(aov_model)

# Box plots of PartResistance by Temperature and Pressure
library(ggplot2)
library(plotly)

# Determine appropriate x-axis and fill variables based on unique factor levels
num_unique_temps <- length(unique(X037..1.$Temperature_Factor))
num_unique_pressures <- length(unique(X037..1.$Pressure_Factor))

if (num_unique_temps > 1 && num_unique_pressures > 1) {
    X037..1.$Temp_Pres_Combination <- interaction(X037..1.$Temperature_Factor, X037..1.$Pressure_Factor, sep = "_")
    x_var <- "Temp_Pres_Combination"
    fill_var <- "Temperature_Factor"
    x_label <- "Temperature_Pressure Combination"
    plot_title <- "Part Resistance by Temperature and Pressure"
} else if (num_unique_temps > 1) {
    x_var <- "Temperature_Factor"
    fill_var <- "Temperature_Factor"
    x_label <- "Temperature"
    plot_title <- "Part Resistance by Temperature"
} else if (num_unique_pressures > 1) {
    x_var <- "Pressure_Factor"
    fill_var <- "Pressure_Factor"
    x_label <- "Pressure"
    plot_title <- "Part Resistance by Pressure"
} else {
    x_var <- "1"
    fill_var <- "1"
    x_label <- "Overall"
    plot_title <- "Overall Part Resistance"
}

p <- ggplot(X037..1., aes_string(x = x_var, y = "PartResistance", fill = fill_var)) +
  geom_boxplot(outlier.colour = "#D55E00") +
  labs(
    title = plot_title,
    x = x_label,
    y = expression("Part Resistance")
  ) +
  theme_minimal() +
  theme(
    axis.title.x = element_text(size = 18),
    axis.title.y = element_text(size = 18),
    axis.text.x = element_text(size = 14, angle = 45, hjust = 1),
    axis.text.y = element_text(size = 14),
    plot.background = element_rect(fill = "white", colour = NA),
    legend.position = "bottom"),
    title = element_text(size = 20)
  ) +
  scale_fill_manual(values = c("#0072B2", "#D55E00", "#009E73", "#CC79A7", "#F0E442", "#56B4E9", "#E69F00"))

fig <- ggplotly(p)
htmlwidgets::saveWidget(fig, "media/plots/resistance_boxplot.html", selfcontained = TRUE)

