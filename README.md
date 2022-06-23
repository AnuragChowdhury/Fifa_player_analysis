# Fifa_player_analysis
We have a dataset which contains information about players in FIFA 21. So, it is actually a dataset of the esports category. We got the dataset from Kaagle. 
The link to the dataset is - (https://www.kaggle.com/aayushmishra1512/fifa-2021-complete-player-data).
We will try to analyze different aspects as much as we can from the dataset we have and we will be using numpy, pandas,matplotlib and seaborn mainly for the analysis.

<iframe src="https://jovian.ai/embed?url=https://jovian.ai/sayakpm3/fifa-21-players-data-analysis-in-python1/v/20&cellId=1-118" title="Jovian Viewer" height="800" width="100%" style="margin 0 auto; max-width: 800px;" frameborder="0" scrolling="auto"></iframe>

{
  "cells": [
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "dmxy10rUFtJr"
      },
      "source": [
        "# Fifa 21 Players Data Analysis in Python.\n",
        "\n",
        "We have a dataset which contains information about players in FIFA 21. So, it is actually a dataset of the esports category. We got the dataset from Kaagle. The link to the dataset is - (https://www.kaggle.com/aayushmishra1512/fifa-2021-complete-player-data).  We will try to analyze different aspects as much as we can from the dataset we have  and we will be using numpy, pandas,matplotlib and seaborn mainly for the analysis. I learned data analysis from the free course organised by jovian in collaboration with freecodecamp. The link to the course is - (http://zerotopandas.com).\n",
        "\n",
        "As a first step, let's upload our Jupyter notebook to [Jovian.ml](https://jovian.ml)."
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "tgBos-3OFtJu"
      },
      "outputs": [],
      "source": [
        "project_name = \"fifa_21_players_data_analysis_in_python1\""
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "1s8XgRXSFtKD"
      },
      "outputs": [],
      "source": [
        "!pip install jovian --upgrade -q"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "CTcnQVGUFtKR"
      },
      "outputs": [],
      "source": [
        "import jovian"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 127
        },
        "id": "ClotPpisFtKd",
        "outputId": "c426fc38-1604-4b3f-9293-9f7bdc766b2e"
      },
      "outputs": [
        {
          "data": {
            "application/javascript": [
              "window.require && require([\"base/js/namespace\"],function(Jupyter){Jupyter.notebook.save_checkpoint()})"
            ],
            "text/plain": [
              "<IPython.core.display.Javascript object>"
            ]
          },
          "metadata": {},
          "output_type": "display_data"
        },
        {
          "name": "stdout",
          "output_type": "stream",
          "text": [
            "[jovian] Attempting to save notebook..\n",
            "[jovian] Updating notebook \"sayakpm3/fifa-21-players-data-analysis-in-python1\" on https://jovian.ml/\n",
            "[jovian] Uploading notebook..\n",
            "[jovian] Capturing environment..\n",
            "[jovian] Committed successfully! https://jovian.ml/sayakpm3/fifa-21-players-data-analysis-in-python1\n"
          ]
        },
        {
          "data": {
            "text/plain": [
              "'https://jovian.ml/sayakpm3/fifa-21-players-data-analysis-in-python1'"
            ]
          },
          "execution_count": 4,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "jovian.commit(project='fifa_21_players_data_analysis_in_python1')"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "428bboFlFtKu"
      },
      "source": [
        "## Data Preparation and Cleaning\n",
        "\n",
        "First we have to read the CSV file using Pandas. Sometimes datasets contain many unwanted values or ambiguous values, so we need to clean them up. \n",
        "After cleaning the data we will prepare the data as per our use."
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "h-pO3fenFtKx"
      },
      "outputs": [],
      "source": [
        "import pandas as pd\n",
        "import numpy as np "
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "EyjjhKyhFtLA"
      },
      "outputs": [],
      "source": [
        "dataraw_df =  pd.read_csv('FIFA 21.csv',delimiter = ';')"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 424
        },
        "id": "6WKnif-yFtLL",
        "outputId": "9f0e2b1b-e07d-4a54-cbe6-981e2a53445f"
      },
      "outputs": [
        {
          "data": {
            "text/html": [
              "<div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>player_id</th>\n",
              "      <th>name</th>\n",
              "      <th>nationality</th>\n",
              "      <th>position</th>\n",
              "      <th>overall</th>\n",
              "      <th>age</th>\n",
              "      <th>hits</th>\n",
              "      <th>potential</th>\n",
              "      <th>team</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>0</th>\n",
              "      <td>158023</td>\n",
              "      <td>Lionel Messi</td>\n",
              "      <td>Argentina</td>\n",
              "      <td>ST|CF|RW</td>\n",
              "      <td>94</td>\n",
              "      <td>33</td>\n",
              "      <td>299</td>\n",
              "      <td>94</td>\n",
              "      <td>FC Barcelona</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>1</th>\n",
              "      <td>20801</td>\n",
              "      <td>Cristiano Ronaldo</td>\n",
              "      <td>Portugal</td>\n",
              "      <td>ST|LW</td>\n",
              "      <td>93</td>\n",
              "      <td>35</td>\n",
              "      <td>276</td>\n",
              "      <td>93</td>\n",
              "      <td>Juventus</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>2</th>\n",
              "      <td>190871</td>\n",
              "      <td>Neymar Jr</td>\n",
              "      <td>Brazil</td>\n",
              "      <td>CAM|LW</td>\n",
              "      <td>92</td>\n",
              "      <td>28</td>\n",
              "      <td>186</td>\n",
              "      <td>92</td>\n",
              "      <td>Paris Saint-Germain</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>3</th>\n",
              "      <td>203376</td>\n",
              "      <td>Virgil van Dijk</td>\n",
              "      <td>Netherlands</td>\n",
              "      <td>CB</td>\n",
              "      <td>91</td>\n",
              "      <td>29</td>\n",
              "      <td>127</td>\n",
              "      <td>92</td>\n",
              "      <td>Liverpool</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>4</th>\n",
              "      <td>200389</td>\n",
              "      <td>Jan Oblak</td>\n",
              "      <td>Slovenia</td>\n",
              "      <td>GK</td>\n",
              "      <td>91</td>\n",
              "      <td>27</td>\n",
              "      <td>47</td>\n",
              "      <td>93</td>\n",
              "      <td>Atlético Madrid</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>...</th>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17976</th>\n",
              "      <td>256093</td>\n",
              "      <td>Jaime Ortíz</td>\n",
              "      <td>Ecuador</td>\n",
              "      <td>ST</td>\n",
              "      <td>56</td>\n",
              "      <td>21</td>\n",
              "      <td>0</td>\n",
              "      <td>64</td>\n",
              "      <td>Sociedad Deportiva Aucas</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17977</th>\n",
              "      <td>256088</td>\n",
              "      <td>Michael Carcelén</td>\n",
              "      <td>Ecuador</td>\n",
              "      <td>CM</td>\n",
              "      <td>56</td>\n",
              "      <td>23</td>\n",
              "      <td>0</td>\n",
              "      <td>64</td>\n",
              "      <td>Club Deportivo El Nacional</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17978</th>\n",
              "      <td>256074</td>\n",
              "      <td>Davide Luzi</td>\n",
              "      <td>Venezuela</td>\n",
              "      <td>ST</td>\n",
              "      <td>56</td>\n",
              "      <td>18</td>\n",
              "      <td>1</td>\n",
              "      <td>68</td>\n",
              "      <td>Zamora Fútbol Club</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17979</th>\n",
              "      <td>256073</td>\n",
              "      <td>Sergio Sulbarán</td>\n",
              "      <td>Venezuela</td>\n",
              "      <td>RW</td>\n",
              "      <td>56</td>\n",
              "      <td>22</td>\n",
              "      <td>0</td>\n",
              "      <td>62</td>\n",
              "      <td>Zamora Fútbol Club</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17980</th>\n",
              "      <td>256072</td>\n",
              "      <td>Luis Peña</td>\n",
              "      <td>Venezuela</td>\n",
              "      <td>CM</td>\n",
              "      <td>56</td>\n",
              "      <td>18</td>\n",
              "      <td>0</td>\n",
              "      <td>69</td>\n",
              "      <td>Zamora Fútbol Club</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "<p>17981 rows × 9 columns</p>\n",
              "</div>"
            ],
            "text/plain": [
              "       player_id               name  nationality  position  overall  age  \\\n",
              "0         158023       Lionel Messi    Argentina  ST|CF|RW       94   33   \n",
              "1          20801  Cristiano Ronaldo     Portugal     ST|LW       93   35   \n",
              "2         190871          Neymar Jr       Brazil    CAM|LW       92   28   \n",
              "3         203376    Virgil van Dijk  Netherlands        CB       91   29   \n",
              "4         200389          Jan Oblak     Slovenia        GK       91   27   \n",
              "...          ...                ...          ...       ...      ...  ...   \n",
              "17976     256093        Jaime Ortíz      Ecuador        ST       56   21   \n",
              "17977     256088   Michael Carcelén      Ecuador        CM       56   23   \n",
              "17978     256074        Davide Luzi    Venezuela        ST       56   18   \n",
              "17979     256073    Sergio Sulbarán    Venezuela        RW       56   22   \n",
              "17980     256072          Luis Peña    Venezuela        CM       56   18   \n",
              "\n",
              "       hits  potential                         team  \n",
              "0       299         94                FC Barcelona   \n",
              "1       276         93                    Juventus   \n",
              "2       186         92         Paris Saint-Germain   \n",
              "3       127         92                   Liverpool   \n",
              "4        47         93             Atlético Madrid   \n",
              "...     ...        ...                          ...  \n",
              "17976     0         64    Sociedad Deportiva Aucas   \n",
              "17977     0         64  Club Deportivo El Nacional   \n",
              "17978     1         68          Zamora Fútbol Club   \n",
              "17979     0         62          Zamora Fútbol Club   \n",
              "17980     0         69          Zamora Fútbol Club   \n",
              "\n",
              "[17981 rows x 9 columns]"
            ]
          },
          "execution_count": 7,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "dataraw_df"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 35
        },
        "id": "Ah177o5jFtLV",
        "outputId": "ddd13d6b-adfd-48b7-9630-e2969911b8b8"
      },
      "outputs": [
        {
          "data": {
            "text/plain": [
              "(17981, 9)"
            ]
          },
          "execution_count": 8,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "dataraw_df.shape"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 72
        },
        "id": "O1QaQAsfFtLg",
        "outputId": "c6deae9c-87bf-48e3-99c5-3a3b32fbbc87"
      },
      "outputs": [
        {
          "data": {
            "text/plain": [
              "Index(['player_id', 'name', 'nationality', 'position', 'overall', 'age',\n",
              "       'hits', 'potential', 'team'],\n",
              "      dtype='object')"
            ]
          },
          "execution_count": 9,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "dataraw_df.columns"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 308
        },
        "id": "tdheBz1BFtLr",
        "outputId": "580af598-717c-443c-c719-b102a2458271"
      },
      "outputs": [
        {
          "name": "stdout",
          "output_type": "stream",
          "text": [
            "<class 'pandas.core.frame.DataFrame'>\n",
            "RangeIndex: 17981 entries, 0 to 17980\n",
            "Data columns (total 9 columns):\n",
            " #   Column       Non-Null Count  Dtype \n",
            "---  ------       --------------  ----- \n",
            " 0   player_id    17981 non-null  int64 \n",
            " 1   name         17981 non-null  object\n",
            " 2   nationality  17981 non-null  object\n",
            " 3   position     17981 non-null  object\n",
            " 4   overall      17981 non-null  int64 \n",
            " 5   age          17981 non-null  int64 \n",
            " 6   hits         17981 non-null  int64 \n",
            " 7   potential    17981 non-null  int64 \n",
            " 8   team         17981 non-null  object\n",
            "dtypes: int64(5), object(4)\n",
            "memory usage: 1.2+ MB\n"
          ]
        }
      ],
      "source": [
        "dataraw_df.info()"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 300
        },
        "id": "6tCfML73FtL2",
        "outputId": "05c24a29-51c5-484f-8f80-632be4a02234"
      },
      "outputs": [
        {
          "data": {
            "text/html": [
              "<div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>player_id</th>\n",
              "      <th>overall</th>\n",
              "      <th>age</th>\n",
              "      <th>hits</th>\n",
              "      <th>potential</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>count</th>\n",
              "      <td>17981.000000</td>\n",
              "      <td>17981.000000</td>\n",
              "      <td>17981.000000</td>\n",
              "      <td>17981.000000</td>\n",
              "      <td>17981.000000</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>mean</th>\n",
              "      <td>220912.660531</td>\n",
              "      <td>67.274345</td>\n",
              "      <td>26.311440</td>\n",
              "      <td>2.689450</td>\n",
              "      <td>71.738057</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>std</th>\n",
              "      <td>27738.072671</td>\n",
              "      <td>5.924392</td>\n",
              "      <td>4.556077</td>\n",
              "      <td>10.846286</td>\n",
              "      <td>5.961968</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>min</th>\n",
              "      <td>41.000000</td>\n",
              "      <td>56.000000</td>\n",
              "      <td>17.000000</td>\n",
              "      <td>0.000000</td>\n",
              "      <td>57.000000</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>25%</th>\n",
              "      <td>204881.000000</td>\n",
              "      <td>63.000000</td>\n",
              "      <td>23.000000</td>\n",
              "      <td>0.000000</td>\n",
              "      <td>67.000000</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>50%</th>\n",
              "      <td>226753.000000</td>\n",
              "      <td>67.000000</td>\n",
              "      <td>26.000000</td>\n",
              "      <td>0.000000</td>\n",
              "      <td>71.000000</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>75%</th>\n",
              "      <td>241587.000000</td>\n",
              "      <td>71.000000</td>\n",
              "      <td>30.000000</td>\n",
              "      <td>2.000000</td>\n",
              "      <td>76.000000</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>max</th>\n",
              "      <td>256469.000000</td>\n",
              "      <td>94.000000</td>\n",
              "      <td>43.000000</td>\n",
              "      <td>371.000000</td>\n",
              "      <td>95.000000</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>"
            ],
            "text/plain": [
              "           player_id       overall           age          hits     potential\n",
              "count   17981.000000  17981.000000  17981.000000  17981.000000  17981.000000\n",
              "mean   220912.660531     67.274345     26.311440      2.689450     71.738057\n",
              "std     27738.072671      5.924392      4.556077     10.846286      5.961968\n",
              "min        41.000000     56.000000     17.000000      0.000000     57.000000\n",
              "25%    204881.000000     63.000000     23.000000      0.000000     67.000000\n",
              "50%    226753.000000     67.000000     26.000000      0.000000     71.000000\n",
              "75%    241587.000000     71.000000     30.000000      2.000000     76.000000\n",
              "max    256469.000000     94.000000     43.000000    371.000000     95.000000"
            ]
          },
          "execution_count": 11,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "dataraw_df.describe()"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "AUdlLXzAFtMC"
      },
      "source": [
        "The information that we got till now :\n",
        "The datasets of Fifa 21 contains 9 columns and 17981 rows. Which means that, there are 17981 players in Fifa 21.\n",
        "The columns contain information like : 'Player id', 'Player Name', 'Player Nationality', 'Position where the player plays', 'Overall rating of the Player', 'Player Age','Player hits', 'Player potential', 'Club for which he plays'\n",
        "The minimum and maximum overall rating of a player in Fifa 21 is 56 and 94 respectively.\n",
        "The minimum and maximum age of a player in Fifa 21 is 17 and 43 respectively."
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 816
        },
        "id": "fPZTIwDLFtMF",
        "outputId": "3d466337-8684-4ba4-fae4-68572a726dbc"
      },
      "outputs": [
        {
          "data": {
            "text/plain": [
              "array(['ST|CF|RW', 'ST|LW', 'CAM|LW', 'CB', 'GK', 'CM|CAM', 'ST', 'ST|RW',\n",
              "       'LW', 'ST|RW|LW', 'CDM|CM', 'ST|CF|LW', 'CM', 'RW|LW', 'CF', 'CDM',\n",
              "       'ST|LM', 'ST|CF', 'CM|CAM|RW', 'RB|CDM|CM', 'CAM|CF', 'LM|CF',\n",
              "       'RM|CM|CAM', 'RM|LM|CAM', 'LB', 'CAM|RW', 'CB|CDM', 'RM|RW',\n",
              "       'LM|CF|LW', 'RM|LM|CM', 'ST|CAM|CF', 'RB', 'CDM|CM|CAM',\n",
              "       'ST|RM|CAM', 'LB|LM|CM', 'RM|LM|RW', 'CM|CAM|CF', 'RM|CM',\n",
              "       'CM|CAM|LW', 'RM|CAM|RW', 'LB|CB', 'RM|CAM', 'RM|LM|LW',\n",
              "       'LM|CM|CAM', 'CAM|CF|LW', 'LB|LM', 'LM|RW|LW', 'RB|LB|CB', 'RM|LM',\n",
              "       'ST|CAM', 'LWB|LM|LW', 'LM', 'RM', 'RM|CF|RW', 'RM|LM|CF',\n",
              "       'RB|RM|RW', 'LB|CB|CDM', 'CAM|RW|LW', 'LM|LW', 'CDM|LM|CM',\n",
              "       'RB|LB|RM', 'RWB|RB|RW', 'CB|CDM|CM', 'RB|CB', 'LB|LW', 'ST|RM|RW',\n",
              "       'ST|RM', 'LM|CAM', 'RM|CF', 'RB|CM', 'RWB|RM|RW', 'RB|RM',\n",
              "       'RM|RW|LW', 'LM|CAM|LW', 'LM|CM', 'ST|RM|LM', 'RWB|RB|LB|RW',\n",
              "       'LB|LWB|LW', 'RW', 'CAM', 'RB|LB|CM', 'ST|LM|CF', 'ST|CM|CAM',\n",
              "       'CF|RW|LW', 'CF|LW', 'ST|LM|LW', 'CM|LW', 'RWB|RW', 'RB|RM|CM',\n",
              "       'ST|CAM|LW', 'LWB|LW', 'RWB|RB|RM|RW', 'RB|LB|LM', 'LB|LWB|LM|LW',\n",
              "       'RB|LB', 'RM|CAM|CF', 'CDM|RM|CM', 'RB|RW', 'CF|RW', 'RM|CAM|LW',\n",
              "       'CM|CF', 'LB|CDM', 'CB|CM', 'LB|CB|LM', 'CDM|CAM', 'RWB|RB|CB|RW',\n",
              "       'LM|CM|LW', 'LB|RM|LM', 'CAM|CF|RW', 'RB|CB|RM', 'LB|CDM|CM',\n",
              "       'RB|RM|LM', 'RB|CDM', 'RWB|CDM|RW', 'LB|LM|CAM', 'ST|CAM|RW',\n",
              "       'LWB|RW|LW', 'ST|LM|CAM', 'RB|CB|CDM', 'CM|CF|LW', 'RWB|RM|LM|RW',\n",
              "       'RM|LW', 'LWB|LM|CM|LW', 'LB|LM|LW', 'CM|RW|LW', 'RM|CM|RW',\n",
              "       'RWB|RM|CM|RW', 'LB|CB|LWB|LW', 'ST|LM|RW', 'LB|CM', 'ST|RM|LW',\n",
              "       'RWB|RB|LWB|RW|LW', 'CDM|CM|LW', 'LWB|RM|LW', 'RB|CB|CM',\n",
              "       'RWB|RM|CAM|RW', 'CB|CF', 'RB|RM|CAM', 'LWB|CM|LW', 'RB|RW|LW',\n",
              "       'LB|RW', 'LB|CM|LW', 'RB|RM|LW', 'RB|CDM|RM', 'ST|CM|LW',\n",
              "       'LM|CAM|CF', 'CB|LWB|LW', 'ST|CM', 'RB|CAM', 'ST|RM|CF',\n",
              "       'LB|LWB|RM|LW', 'CM|RW', 'LWB|RM|RW|LW', 'CDM|RM', 'LWB|RM|LM|LW',\n",
              "       'RWB|CB|CM|RW', 'RB|LB|CDM', 'CB|CM|CAM', 'LM|CAM|RW', 'ST|LM|CM',\n",
              "       'CDM|LM', 'RWB|RW|LW', 'RWB|CB|RW', 'ST|CM|RW', 'CDM|RM|LM',\n",
              "       'ST|CB|CAM', 'RB|LWB|LM|LW', 'RM|CM|CF', 'CDM|CAM|CF', 'ST|CM|CF',\n",
              "       'RM|CM|LW', 'LB|LWB|CDM|LW', 'LB|LWB|CM|LW', 'ST|RB|RM',\n",
              "       'RB|LB|LWB|LW', 'ST|LB|LM', 'ST|RB|CM', 'RWB|RB|LM|RW',\n",
              "       'ST|RWB|RM|RW', 'CDM|LM|CAM', 'RWB|CDM|CM|RW', 'RWB|CM|RW',\n",
              "       'RWB|LWB|RM|RW|LW', 'LB|CDM|LM', 'RWB|RB|CDM|RW', 'LB|RM',\n",
              "       'ST|RM|CM', 'RB|CB|LM', 'ST|LWB|LW', 'CB|LM', 'ST|CDM|CM',\n",
              "       'LB|CM|CAM', 'ST|CB', 'LM|RW', 'RB|LB|RW', 'ST|RB|RW',\n",
              "       'RWB|CB|RM|RW', 'CB|LWB|LM|LW', 'CDM|CM|RW', 'RB|LM|CM',\n",
              "       'RB|CDM|CAM', 'RWB|RB|CM|RW', 'LWB|CM|CAM|LW', 'RWB|LWB|RW|LW',\n",
              "       'ST|RB', 'LM|CM|RW', 'RWB|CM|CAM|RW', 'CB|RW', 'ST|RB|LM',\n",
              "       'ST|RB|CB', 'ST|LWB|LM|LW', 'LB|CAM', 'RB|LM', 'GK|RB', 'LB|RM|CM',\n",
              "       'RB|CM|RW', 'RWB|LB|LWB|RW|LW', 'RB|RM|CF', 'RWB|LWB|CM|RW|LW',\n",
              "       'RWB|LB|RM|RW', 'LM|CM|CF', 'RB|CDM|RW', 'CDM|LM|LW', 'CB|RM',\n",
              "       'ST|RWB|RW', 'RWB|LB|RW', 'ST|CDM', 'RB|LWB|LW',\n",
              "       'RWB|LWB|LM|RW|LW', 'CDM|RM|CAM', 'RWB|CB|LWB|RW|LW', 'CB|RM|LM'],\n",
              "      dtype=object)"
            ]
          },
          "execution_count": 12,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "dataraw_df.position.unique()"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 35
        },
        "id": "5bP-eKKPFtMO",
        "outputId": "b350dd71-c8a5-4f17-90a5-9cd8c3cb1787"
      },
      "outputs": [
        {
          "data": {
            "text/plain": [
              "232"
            ]
          },
          "execution_count": 13,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "dataraw_df.position.nunique() # Counting the number of unique positions in Fifa 21"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "oWoaQnpPFtMX"
      },
      "source": [
        "### Preparing the data according to our need.\n",
        "Here, we can observe that there are 232 different combinations of positions that the players plays in. The position data is actually very diversified. For our convenience we will categorize the positions broadly as 'forwards', 'midfielders', 'defenders' and goalkeepers. In 'forward' category we will keep the positions - 'ST', 'CF', 'LW', 'RW', 'LF', 'RF', and 'combinations of the above mentioned positions'. Same thing we will do for 'midfielders', 'defenders' and 'goalkeepers'. We will create different data sets for the forwards, midfielders, defenders and goalkeepers.\n",
        "This is actually the preparation of the data that we need to do to analyse the choosen dataset."
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "P_p5x7AiFtMa"
      },
      "outputs": [],
      "source": [
        "#Creating the dataframe that consists 'forwards'. \n",
        "forwards_df = dataraw_df[(dataraw_df.position == 'ST|CF|RW') | \n",
        "                         (dataraw_df.position == 'ST|LW') | \n",
        "                         (dataraw_df.position == 'ST|CF|LW') | \n",
        "                         (dataraw_df.position == 'ST|CF') |\n",
        "                         (dataraw_df.position == 'ST|RW') |\n",
        "                         (dataraw_df.position == 'LW') |\n",
        "                         (dataraw_df.position == 'RW') |\n",
        "                         (dataraw_df.position == 'ST|RW|LW') |\n",
        "                         (dataraw_df.position == 'ST|CF|LW') |\n",
        "                         (dataraw_df.position == 'ST') |\n",
        "                         (dataraw_df.position == 'CF') |\n",
        "                         (dataraw_df.position == 'LF') |\n",
        "                         (dataraw_df.position == 'RF') |\n",
        "                         (dataraw_df.position == 'ST|CF') |\n",
        "                         (dataraw_df.position == 'RW|LW') |\n",
        "                         (dataraw_df.position == 'CF|RW|LW') |\n",
        "                         (dataraw_df.position == 'CF|LW') |\n",
        "                         (dataraw_df.position == 'CAM|LW')\n",
        "                        ]\n",
        "                         "
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "rJpxMGVCFtMi"
      },
      "outputs": [],
      "source": [
        "#Creating the dataframe that consists 'midfielders'. \n",
        "midfielders_df = dataraw_df[(dataraw_df.position == 'LM') | \n",
        "                         (dataraw_df.position == 'RM') | \n",
        "                         (dataraw_df.position == 'CM') | \n",
        "                         (dataraw_df.position == 'CDM') |\n",
        "                         (dataraw_df.position == 'DM') |\n",
        "                         (dataraw_df.position == 'AM') |\n",
        "                         (dataraw_df.position == 'CAM') |\n",
        "                         (dataraw_df.position == 'CM|CAM') |\n",
        "                         (dataraw_df.position == 'CDM|CM') |\n",
        "                         (dataraw_df.position == 'RM|CM|CAM') |\n",
        "                         (dataraw_df.position == 'RM|LM|CAM') |\n",
        "                         (dataraw_df.position == 'CDM|CM|CAM') |\n",
        "                         (dataraw_df.position == 'RM|CM') |\n",
        "                         (dataraw_df.position == 'RM|CAM') |\n",
        "                         (dataraw_df.position == 'LM|CM|CAM') |\n",
        "                         (dataraw_df.position == 'RM|LM') |\n",
        "                         (dataraw_df.position == 'CDM|LM|CM') |\n",
        "                         (dataraw_df.position == 'CDM|LM') |\n",
        "                         (dataraw_df.position == 'CDM|LM|CAM') |\n",
        "                         (dataraw_df.position == 'CDM|RM') |\n",
        "                         (dataraw_df.position == 'CDM|RM|CAM')\n",
        "                           ]\n",
        "                 "
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "7CNCP0mgFtMr"
      },
      "outputs": [],
      "source": [
        "#Creating the dataframe that consists 'defenders'. \n",
        "defenders_df = dataraw_df[(dataraw_df.position == 'CB') | \n",
        "                         (dataraw_df.position == 'LB') | \n",
        "                         (dataraw_df.position == 'RB') | \n",
        "                         (dataraw_df.position == 'LB|CB') |\n",
        "                         (dataraw_df.position == 'RB|LB|CB') |\n",
        "                         (dataraw_df.position == 'RB|CB') \n",
        "                         ]\n",
        "                          "
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "EBpw_DNcFtMz"
      },
      "outputs": [],
      "source": [
        "#Creating the dataframe that consists 'goalkeepers'. \n",
        "gk_df = dataraw_df[(dataraw_df.position == 'GK') ]"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "AabbwGOjFtM8"
      },
      "outputs": [],
      "source": [
        "import jovian"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 90
        },
        "id": "B-5ncAXgFtND",
        "outputId": "e82e636e-57d8-4914-90df-a355c016a9e4"
      },
      "outputs": [
        {
          "data": {
            "application/javascript": [
              "window.require && require([\"base/js/namespace\"],function(Jupyter){Jupyter.notebook.save_checkpoint()})"
            ],
            "text/plain": [
              "<IPython.core.display.Javascript object>"
            ]
          },
          "metadata": {},
          "output_type": "display_data"
        },
        {
          "name": "stdout",
          "output_type": "stream",
          "text": [
            "[jovian] Attempting to save notebook..\n",
            "[jovian] Updating notebook \"sayakpm3/fifa-21-players-data-analysis-in-python1\" on https://jovian.ml/\n",
            "[jovian] Uploading notebook..\n",
            "[jovian] Capturing environment..\n",
            "[jovian] Committed successfully! https://jovian.ml/sayakpm3/fifa-21-players-data-analysis-in-python1\n"
          ]
        },
        {
          "data": {
            "text/plain": [
              "'https://jovian.ml/sayakpm3/fifa-21-players-data-analysis-in-python1'"
            ]
          },
          "execution_count": 19,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "jovian.commit(project='fifa_21_players_data_analysis_in_python1')"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "Gejz4QfwFtNP"
      },
      "source": [
        "## Exploratory Analysis and Visualization\n",
        "\n",
        "After we are done with data cleaning, we can make insightful and interesting analysis on that data. Here we will do just the same thing, we will try to get a good visual representation of the data. We will use pandas methods and functions to dig more into the dataset and analyse the data as best as we can."
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "sadQZx2sFtNS"
      },
      "outputs": [],
      "source": [
        "!pip install matplotlib seaborn --upgrade --quiet"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "2YfRyfOjFtNd"
      },
      "outputs": [],
      "source": [
        "import seaborn as sns\n",
        "import matplotlib\n",
        "import matplotlib.pyplot as plt\n",
        "sns.set_style('whitegrid')\n",
        "matplotlib.rcParams['font.size'] = 14\n",
        "matplotlib.rcParams['figure.figsize'] = (9, 5)\n",
        "matplotlib.rcParams['figure.facecolor'] = '#00000000'\n",
        "%matplotlib inline"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 424
        },
        "id": "LxNBcVkzFtNk",
        "outputId": "028cb94a-a71f-4606-8a29-c6c856e8759f"
      },
      "outputs": [
        {
          "data": {
            "text/html": [
              "<div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>player_id</th>\n",
              "      <th>name</th>\n",
              "      <th>nationality</th>\n",
              "      <th>position</th>\n",
              "      <th>overall</th>\n",
              "      <th>age</th>\n",
              "      <th>hits</th>\n",
              "      <th>potential</th>\n",
              "      <th>team</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>0</th>\n",
              "      <td>158023</td>\n",
              "      <td>Lionel Messi</td>\n",
              "      <td>Argentina</td>\n",
              "      <td>ST|CF|RW</td>\n",
              "      <td>94</td>\n",
              "      <td>33</td>\n",
              "      <td>299</td>\n",
              "      <td>94</td>\n",
              "      <td>FC Barcelona</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>1</th>\n",
              "      <td>20801</td>\n",
              "      <td>Cristiano Ronaldo</td>\n",
              "      <td>Portugal</td>\n",
              "      <td>ST|LW</td>\n",
              "      <td>93</td>\n",
              "      <td>35</td>\n",
              "      <td>276</td>\n",
              "      <td>93</td>\n",
              "      <td>Juventus</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>2</th>\n",
              "      <td>190871</td>\n",
              "      <td>Neymar Jr</td>\n",
              "      <td>Brazil</td>\n",
              "      <td>CAM|LW</td>\n",
              "      <td>92</td>\n",
              "      <td>28</td>\n",
              "      <td>186</td>\n",
              "      <td>92</td>\n",
              "      <td>Paris Saint-Germain</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>6</th>\n",
              "      <td>188545</td>\n",
              "      <td>Robert Lewandowski</td>\n",
              "      <td>Poland</td>\n",
              "      <td>ST</td>\n",
              "      <td>91</td>\n",
              "      <td>31</td>\n",
              "      <td>89</td>\n",
              "      <td>91</td>\n",
              "      <td>FC Bayern München</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>7</th>\n",
              "      <td>183277</td>\n",
              "      <td>Eden Hazard</td>\n",
              "      <td>Belgium</td>\n",
              "      <td>ST|LW</td>\n",
              "      <td>91</td>\n",
              "      <td>29</td>\n",
              "      <td>66</td>\n",
              "      <td>91</td>\n",
              "      <td>Real Madrid</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>...</th>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17968</th>\n",
              "      <td>256326</td>\n",
              "      <td>Paulos Abraham</td>\n",
              "      <td>Sweden</td>\n",
              "      <td>RW|LW</td>\n",
              "      <td>56</td>\n",
              "      <td>18</td>\n",
              "      <td>1</td>\n",
              "      <td>71</td>\n",
              "      <td>AIK</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17969</th>\n",
              "      <td>256314</td>\n",
              "      <td>Gautier Ott</td>\n",
              "      <td>France</td>\n",
              "      <td>ST</td>\n",
              "      <td>56</td>\n",
              "      <td>18</td>\n",
              "      <td>0</td>\n",
              "      <td>75</td>\n",
              "      <td>AS Nancy Lorraine</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17976</th>\n",
              "      <td>256093</td>\n",
              "      <td>Jaime Ortíz</td>\n",
              "      <td>Ecuador</td>\n",
              "      <td>ST</td>\n",
              "      <td>56</td>\n",
              "      <td>21</td>\n",
              "      <td>0</td>\n",
              "      <td>64</td>\n",
              "      <td>Sociedad Deportiva Aucas</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17978</th>\n",
              "      <td>256074</td>\n",
              "      <td>Davide Luzi</td>\n",
              "      <td>Venezuela</td>\n",
              "      <td>ST</td>\n",
              "      <td>56</td>\n",
              "      <td>18</td>\n",
              "      <td>1</td>\n",
              "      <td>68</td>\n",
              "      <td>Zamora Fútbol Club</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17979</th>\n",
              "      <td>256073</td>\n",
              "      <td>Sergio Sulbarán</td>\n",
              "      <td>Venezuela</td>\n",
              "      <td>RW</td>\n",
              "      <td>56</td>\n",
              "      <td>22</td>\n",
              "      <td>0</td>\n",
              "      <td>62</td>\n",
              "      <td>Zamora Fútbol Club</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "<p>2581 rows × 9 columns</p>\n",
              "</div>"
            ],
            "text/plain": [
              "       player_id                name nationality  position  overall  age  \\\n",
              "0         158023        Lionel Messi   Argentina  ST|CF|RW       94   33   \n",
              "1          20801   Cristiano Ronaldo    Portugal     ST|LW       93   35   \n",
              "2         190871           Neymar Jr      Brazil    CAM|LW       92   28   \n",
              "6         188545  Robert Lewandowski      Poland        ST       91   31   \n",
              "7         183277         Eden Hazard     Belgium     ST|LW       91   29   \n",
              "...          ...                 ...         ...       ...      ...  ...   \n",
              "17968     256326      Paulos Abraham      Sweden     RW|LW       56   18   \n",
              "17969     256314         Gautier Ott      France        ST       56   18   \n",
              "17976     256093         Jaime Ortíz     Ecuador        ST       56   21   \n",
              "17978     256074         Davide Luzi   Venezuela        ST       56   18   \n",
              "17979     256073     Sergio Sulbarán   Venezuela        RW       56   22   \n",
              "\n",
              "       hits  potential                       team  \n",
              "0       299         94              FC Barcelona   \n",
              "1       276         93                  Juventus   \n",
              "2       186         92       Paris Saint-Germain   \n",
              "6        89         91         FC Bayern München   \n",
              "7        66         91               Real Madrid   \n",
              "...     ...        ...                        ...  \n",
              "17968     1         71                       AIK   \n",
              "17969     0         75         AS Nancy Lorraine   \n",
              "17976     0         64  Sociedad Deportiva Aucas   \n",
              "17978     1         68        Zamora Fútbol Club   \n",
              "17979     0         62        Zamora Fútbol Club   \n",
              "\n",
              "[2581 rows x 9 columns]"
            ]
          },
          "execution_count": 22,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "#Dataframe containing forwards\n",
        "forwards_df"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "SGo_OgXhFtNu"
      },
      "source": [
        "The original dataset of Fifa 21 is sorted in descending order of overall rating. So for finding top or bottom players on the basis of overall rating we don't need to sort the dataset."
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "CTNql8dQFtNw"
      },
      "source": [
        "Let's look at the 10 forwards with highest overall rating in Fifa 21."
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 363
        },
        "id": "ZuB4YtgxFtNx",
        "outputId": "28ad6c24-890d-43ec-80b9-fbaf883816be"
      },
      "outputs": [
        {
          "data": {
            "text/html": [
              "<div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>player_id</th>\n",
              "      <th>name</th>\n",
              "      <th>nationality</th>\n",
              "      <th>position</th>\n",
              "      <th>overall</th>\n",
              "      <th>age</th>\n",
              "      <th>hits</th>\n",
              "      <th>potential</th>\n",
              "      <th>team</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>0</th>\n",
              "      <td>158023</td>\n",
              "      <td>Lionel Messi</td>\n",
              "      <td>Argentina</td>\n",
              "      <td>ST|CF|RW</td>\n",
              "      <td>94</td>\n",
              "      <td>33</td>\n",
              "      <td>299</td>\n",
              "      <td>94</td>\n",
              "      <td>FC Barcelona</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>1</th>\n",
              "      <td>20801</td>\n",
              "      <td>Cristiano Ronaldo</td>\n",
              "      <td>Portugal</td>\n",
              "      <td>ST|LW</td>\n",
              "      <td>93</td>\n",
              "      <td>35</td>\n",
              "      <td>276</td>\n",
              "      <td>93</td>\n",
              "      <td>Juventus</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>2</th>\n",
              "      <td>190871</td>\n",
              "      <td>Neymar Jr</td>\n",
              "      <td>Brazil</td>\n",
              "      <td>CAM|LW</td>\n",
              "      <td>92</td>\n",
              "      <td>28</td>\n",
              "      <td>186</td>\n",
              "      <td>92</td>\n",
              "      <td>Paris Saint-Germain</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>6</th>\n",
              "      <td>188545</td>\n",
              "      <td>Robert Lewandowski</td>\n",
              "      <td>Poland</td>\n",
              "      <td>ST</td>\n",
              "      <td>91</td>\n",
              "      <td>31</td>\n",
              "      <td>89</td>\n",
              "      <td>91</td>\n",
              "      <td>FC Bayern München</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>7</th>\n",
              "      <td>183277</td>\n",
              "      <td>Eden Hazard</td>\n",
              "      <td>Belgium</td>\n",
              "      <td>ST|LW</td>\n",
              "      <td>91</td>\n",
              "      <td>29</td>\n",
              "      <td>66</td>\n",
              "      <td>91</td>\n",
              "      <td>Real Madrid</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>9</th>\n",
              "      <td>209331</td>\n",
              "      <td>Mohamed Salah</td>\n",
              "      <td>Egypt</td>\n",
              "      <td>ST|RW</td>\n",
              "      <td>90</td>\n",
              "      <td>28</td>\n",
              "      <td>94</td>\n",
              "      <td>90</td>\n",
              "      <td>Liverpool</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>10</th>\n",
              "      <td>208722</td>\n",
              "      <td>Sadio Mané</td>\n",
              "      <td>Senegal</td>\n",
              "      <td>LW</td>\n",
              "      <td>90</td>\n",
              "      <td>28</td>\n",
              "      <td>76</td>\n",
              "      <td>90</td>\n",
              "      <td>Liverpool</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>12</th>\n",
              "      <td>153079</td>\n",
              "      <td>Sergio Agüero</td>\n",
              "      <td>Argentina</td>\n",
              "      <td>ST</td>\n",
              "      <td>90</td>\n",
              "      <td>32</td>\n",
              "      <td>50</td>\n",
              "      <td>90</td>\n",
              "      <td>Manchester City</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>13</th>\n",
              "      <td>231747</td>\n",
              "      <td>Kylian Mbappé</td>\n",
              "      <td>France</td>\n",
              "      <td>ST|RW|LW</td>\n",
              "      <td>89</td>\n",
              "      <td>21</td>\n",
              "      <td>222</td>\n",
              "      <td>95</td>\n",
              "      <td>Paris Saint-Germain</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>15</th>\n",
              "      <td>202126</td>\n",
              "      <td>Harry Kane</td>\n",
              "      <td>England</td>\n",
              "      <td>ST</td>\n",
              "      <td>89</td>\n",
              "      <td>27</td>\n",
              "      <td>64</td>\n",
              "      <td>91</td>\n",
              "      <td>Tottenham Hotspur</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>"
            ],
            "text/plain": [
              "    player_id                name nationality  position  overall  age  hits  \\\n",
              "0      158023        Lionel Messi   Argentina  ST|CF|RW       94   33   299   \n",
              "1       20801   Cristiano Ronaldo    Portugal     ST|LW       93   35   276   \n",
              "2      190871           Neymar Jr      Brazil    CAM|LW       92   28   186   \n",
              "6      188545  Robert Lewandowski      Poland        ST       91   31    89   \n",
              "7      183277         Eden Hazard     Belgium     ST|LW       91   29    66   \n",
              "9      209331       Mohamed Salah       Egypt     ST|RW       90   28    94   \n",
              "10     208722          Sadio Mané     Senegal        LW       90   28    76   \n",
              "12     153079       Sergio Agüero   Argentina        ST       90   32    50   \n",
              "13     231747       Kylian Mbappé      France  ST|RW|LW       89   21   222   \n",
              "15     202126          Harry Kane     England        ST       89   27    64   \n",
              "\n",
              "    potential                  team  \n",
              "0          94         FC Barcelona   \n",
              "1          93             Juventus   \n",
              "2          92  Paris Saint-Germain   \n",
              "6          91    FC Bayern München   \n",
              "7          91          Real Madrid   \n",
              "9          90            Liverpool   \n",
              "10         90            Liverpool   \n",
              "12         90      Manchester City   \n",
              "13         95  Paris Saint-Germain   \n",
              "15         91    Tottenham Hotspur   "
            ]
          },
          "execution_count": 23,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "forwards_df.head(10)"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 424
        },
        "id": "18t8R9LdFtN8",
        "outputId": "23fa9ee8-e26b-4e4b-b108-4a4ce45fba09"
      },
      "outputs": [
        {
          "data": {
            "text/html": [
              "<div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>player_id</th>\n",
              "      <th>name</th>\n",
              "      <th>nationality</th>\n",
              "      <th>position</th>\n",
              "      <th>overall</th>\n",
              "      <th>age</th>\n",
              "      <th>hits</th>\n",
              "      <th>potential</th>\n",
              "      <th>team</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>5</th>\n",
              "      <td>192985</td>\n",
              "      <td>Kevin De Bruyne</td>\n",
              "      <td>Belgium</td>\n",
              "      <td>CM|CAM</td>\n",
              "      <td>91</td>\n",
              "      <td>29</td>\n",
              "      <td>119</td>\n",
              "      <td>91</td>\n",
              "      <td>Manchester City</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>14</th>\n",
              "      <td>215914</td>\n",
              "      <td>N'Golo Kanté</td>\n",
              "      <td>France</td>\n",
              "      <td>CDM|CM</td>\n",
              "      <td>89</td>\n",
              "      <td>29</td>\n",
              "      <td>75</td>\n",
              "      <td>89</td>\n",
              "      <td>Chelsea</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17</th>\n",
              "      <td>182521</td>\n",
              "      <td>Toni Kroos</td>\n",
              "      <td>Germany</td>\n",
              "      <td>CM</td>\n",
              "      <td>89</td>\n",
              "      <td>30</td>\n",
              "      <td>37</td>\n",
              "      <td>89</td>\n",
              "      <td>Real Madrid</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>18</th>\n",
              "      <td>177003</td>\n",
              "      <td>Luka Modric</td>\n",
              "      <td>Croatia</td>\n",
              "      <td>CM</td>\n",
              "      <td>89</td>\n",
              "      <td>34</td>\n",
              "      <td>31</td>\n",
              "      <td>89</td>\n",
              "      <td>Real Madrid</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>26</th>\n",
              "      <td>200145</td>\n",
              "      <td>Casemiro</td>\n",
              "      <td>Brazil</td>\n",
              "      <td>CDM</td>\n",
              "      <td>88</td>\n",
              "      <td>28</td>\n",
              "      <td>37</td>\n",
              "      <td>89</td>\n",
              "      <td>Real Madrid</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>...</th>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17971</th>\n",
              "      <td>256170</td>\n",
              "      <td>Samuel Renel</td>\n",
              "      <td>France</td>\n",
              "      <td>RM|CM|CAM</td>\n",
              "      <td>56</td>\n",
              "      <td>18</td>\n",
              "      <td>0</td>\n",
              "      <td>72</td>\n",
              "      <td>Chamois Niortais Football Club</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17973</th>\n",
              "      <td>256148</td>\n",
              "      <td>Joseph Espinoza</td>\n",
              "      <td>Ecuador</td>\n",
              "      <td>CDM</td>\n",
              "      <td>56</td>\n",
              "      <td>20</td>\n",
              "      <td>0</td>\n",
              "      <td>66</td>\n",
              "      <td>LDU Quito</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17974</th>\n",
              "      <td>256129</td>\n",
              "      <td>Zakaria Atteri</td>\n",
              "      <td>Morocco</td>\n",
              "      <td>CM|CAM</td>\n",
              "      <td>56</td>\n",
              "      <td>19</td>\n",
              "      <td>0</td>\n",
              "      <td>70</td>\n",
              "      <td>Royal Excel Mouscron</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17977</th>\n",
              "      <td>256088</td>\n",
              "      <td>Michael Carcelén</td>\n",
              "      <td>Ecuador</td>\n",
              "      <td>CM</td>\n",
              "      <td>56</td>\n",
              "      <td>23</td>\n",
              "      <td>0</td>\n",
              "      <td>64</td>\n",
              "      <td>Club Deportivo El Nacional</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17980</th>\n",
              "      <td>256072</td>\n",
              "      <td>Luis Peña</td>\n",
              "      <td>Venezuela</td>\n",
              "      <td>CM</td>\n",
              "      <td>56</td>\n",
              "      <td>18</td>\n",
              "      <td>0</td>\n",
              "      <td>69</td>\n",
              "      <td>Zamora Fútbol Club</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "<p>4765 rows × 9 columns</p>\n",
              "</div>"
            ],
            "text/plain": [
              "       player_id              name nationality   position  overall  age  hits  \\\n",
              "5         192985   Kevin De Bruyne     Belgium     CM|CAM       91   29   119   \n",
              "14        215914      N'Golo Kanté      France     CDM|CM       89   29    75   \n",
              "17        182521        Toni Kroos     Germany         CM       89   30    37   \n",
              "18        177003       Luka Modric     Croatia         CM       89   34    31   \n",
              "26        200145          Casemiro      Brazil        CDM       88   28    37   \n",
              "...          ...               ...         ...        ...      ...  ...   ...   \n",
              "17971     256170      Samuel Renel      France  RM|CM|CAM       56   18     0   \n",
              "17973     256148   Joseph Espinoza     Ecuador        CDM       56   20     0   \n",
              "17974     256129    Zakaria Atteri     Morocco     CM|CAM       56   19     0   \n",
              "17977     256088  Michael Carcelén     Ecuador         CM       56   23     0   \n",
              "17980     256072         Luis Peña   Venezuela         CM       56   18     0   \n",
              "\n",
              "       potential                             team  \n",
              "5             91                 Manchester City   \n",
              "14            89                         Chelsea   \n",
              "17            89                     Real Madrid   \n",
              "18            89                     Real Madrid   \n",
              "26            89                     Real Madrid   \n",
              "...          ...                              ...  \n",
              "17971         72  Chamois Niortais Football Club   \n",
              "17973         66                       LDU Quito   \n",
              "17974         70            Royal Excel Mouscron   \n",
              "17977         64      Club Deportivo El Nacional   \n",
              "17980         69              Zamora Fútbol Club   \n",
              "\n",
              "[4765 rows x 9 columns]"
            ]
          },
          "execution_count": 24,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "#Dataframe containing midfielders\n",
        "midfielders_df"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "lZ5rM1l3FtOF"
      },
      "source": [
        "Let's look at the 10 midfielders with highest overall rating in Fifa 21"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 363
        },
        "id": "jFhcfY7PFtOG",
        "outputId": "c2bd2de1-e6f9-42c1-9e00-54c1433968d2"
      },
      "outputs": [
        {
          "data": {
            "text/html": [
              "<div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>player_id</th>\n",
              "      <th>name</th>\n",
              "      <th>nationality</th>\n",
              "      <th>position</th>\n",
              "      <th>overall</th>\n",
              "      <th>age</th>\n",
              "      <th>hits</th>\n",
              "      <th>potential</th>\n",
              "      <th>team</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>5</th>\n",
              "      <td>192985</td>\n",
              "      <td>Kevin De Bruyne</td>\n",
              "      <td>Belgium</td>\n",
              "      <td>CM|CAM</td>\n",
              "      <td>91</td>\n",
              "      <td>29</td>\n",
              "      <td>119</td>\n",
              "      <td>91</td>\n",
              "      <td>Manchester City</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>14</th>\n",
              "      <td>215914</td>\n",
              "      <td>N'Golo Kanté</td>\n",
              "      <td>France</td>\n",
              "      <td>CDM|CM</td>\n",
              "      <td>89</td>\n",
              "      <td>29</td>\n",
              "      <td>75</td>\n",
              "      <td>89</td>\n",
              "      <td>Chelsea</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17</th>\n",
              "      <td>182521</td>\n",
              "      <td>Toni Kroos</td>\n",
              "      <td>Germany</td>\n",
              "      <td>CM</td>\n",
              "      <td>89</td>\n",
              "      <td>30</td>\n",
              "      <td>37</td>\n",
              "      <td>89</td>\n",
              "      <td>Real Madrid</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>18</th>\n",
              "      <td>177003</td>\n",
              "      <td>Luka Modric</td>\n",
              "      <td>Croatia</td>\n",
              "      <td>CM</td>\n",
              "      <td>89</td>\n",
              "      <td>34</td>\n",
              "      <td>31</td>\n",
              "      <td>89</td>\n",
              "      <td>Real Madrid</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>26</th>\n",
              "      <td>200145</td>\n",
              "      <td>Casemiro</td>\n",
              "      <td>Brazil</td>\n",
              "      <td>CDM</td>\n",
              "      <td>88</td>\n",
              "      <td>28</td>\n",
              "      <td>37</td>\n",
              "      <td>89</td>\n",
              "      <td>Real Madrid</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>29</th>\n",
              "      <td>189511</td>\n",
              "      <td>Sergio Busquets</td>\n",
              "      <td>Spain</td>\n",
              "      <td>CDM</td>\n",
              "      <td>88</td>\n",
              "      <td>32</td>\n",
              "      <td>34</td>\n",
              "      <td>88</td>\n",
              "      <td>FC Barcelona</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>40</th>\n",
              "      <td>199556</td>\n",
              "      <td>Marco Verratti</td>\n",
              "      <td>Italy</td>\n",
              "      <td>CDM|CM</td>\n",
              "      <td>87</td>\n",
              "      <td>27</td>\n",
              "      <td>45</td>\n",
              "      <td>88</td>\n",
              "      <td>Paris Saint-Germain</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>41</th>\n",
              "      <td>195864</td>\n",
              "      <td>Paul Pogba</td>\n",
              "      <td>France</td>\n",
              "      <td>CDM|CM</td>\n",
              "      <td>87</td>\n",
              "      <td>27</td>\n",
              "      <td>70</td>\n",
              "      <td>88</td>\n",
              "      <td>Manchester United</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>44</th>\n",
              "      <td>190460</td>\n",
              "      <td>Christian Eriksen</td>\n",
              "      <td>Denmark</td>\n",
              "      <td>RM|CM|CAM</td>\n",
              "      <td>87</td>\n",
              "      <td>28</td>\n",
              "      <td>48</td>\n",
              "      <td>87</td>\n",
              "      <td>Inter</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>45</th>\n",
              "      <td>189513</td>\n",
              "      <td>Parejo</td>\n",
              "      <td>Spain</td>\n",
              "      <td>CM</td>\n",
              "      <td>87</td>\n",
              "      <td>31</td>\n",
              "      <td>14</td>\n",
              "      <td>87</td>\n",
              "      <td>Valencia CF</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>"
            ],
            "text/plain": [
              "    player_id               name nationality   position  overall  age  hits  \\\n",
              "5      192985    Kevin De Bruyne     Belgium     CM|CAM       91   29   119   \n",
              "14     215914       N'Golo Kanté      France     CDM|CM       89   29    75   \n",
              "17     182521         Toni Kroos     Germany         CM       89   30    37   \n",
              "18     177003        Luka Modric     Croatia         CM       89   34    31   \n",
              "26     200145           Casemiro      Brazil        CDM       88   28    37   \n",
              "29     189511    Sergio Busquets       Spain        CDM       88   32    34   \n",
              "40     199556     Marco Verratti       Italy     CDM|CM       87   27    45   \n",
              "41     195864         Paul Pogba      France     CDM|CM       87   27    70   \n",
              "44     190460  Christian Eriksen     Denmark  RM|CM|CAM       87   28    48   \n",
              "45     189513             Parejo       Spain         CM       87   31    14   \n",
              "\n",
              "    potential                  team  \n",
              "5          91      Manchester City   \n",
              "14         89              Chelsea   \n",
              "17         89          Real Madrid   \n",
              "18         89          Real Madrid   \n",
              "26         89          Real Madrid   \n",
              "29         88         FC Barcelona   \n",
              "40         88  Paris Saint-Germain   \n",
              "41         88    Manchester United   \n",
              "44         87                Inter   \n",
              "45         87          Valencia CF   "
            ]
          },
          "execution_count": 25,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "midfielders_df.head(10)"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 424
        },
        "id": "Y4VQgyjJFtOQ",
        "outputId": "dffa368a-3a60-4629-da0a-c54b7cddba4d"
      },
      "outputs": [
        {
          "data": {
            "text/html": [
              "<div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>player_id</th>\n",
              "      <th>name</th>\n",
              "      <th>nationality</th>\n",
              "      <th>position</th>\n",
              "      <th>overall</th>\n",
              "      <th>age</th>\n",
              "      <th>hits</th>\n",
              "      <th>potential</th>\n",
              "      <th>team</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>3</th>\n",
              "      <td>203376</td>\n",
              "      <td>Virgil van Dijk</td>\n",
              "      <td>Netherlands</td>\n",
              "      <td>CB</td>\n",
              "      <td>91</td>\n",
              "      <td>29</td>\n",
              "      <td>127</td>\n",
              "      <td>92</td>\n",
              "      <td>Liverpool</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>21</th>\n",
              "      <td>155862</td>\n",
              "      <td>Sergio Ramos</td>\n",
              "      <td>Spain</td>\n",
              "      <td>CB</td>\n",
              "      <td>89</td>\n",
              "      <td>34</td>\n",
              "      <td>55</td>\n",
              "      <td>89</td>\n",
              "      <td>Real Madrid</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>25</th>\n",
              "      <td>201024</td>\n",
              "      <td>Kalidou Koulibaly</td>\n",
              "      <td>Senegal</td>\n",
              "      <td>CB</td>\n",
              "      <td>88</td>\n",
              "      <td>29</td>\n",
              "      <td>78</td>\n",
              "      <td>90</td>\n",
              "      <td>Napoli</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>33</th>\n",
              "      <td>152729</td>\n",
              "      <td>Piqué</td>\n",
              "      <td>Spain</td>\n",
              "      <td>CB</td>\n",
              "      <td>88</td>\n",
              "      <td>33</td>\n",
              "      <td>41</td>\n",
              "      <td>88</td>\n",
              "      <td>FC Barcelona</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>34</th>\n",
              "      <td>138956</td>\n",
              "      <td>Giorgio Chiellini</td>\n",
              "      <td>Italy</td>\n",
              "      <td>CB</td>\n",
              "      <td>88</td>\n",
              "      <td>35</td>\n",
              "      <td>19</td>\n",
              "      <td>88</td>\n",
              "      <td>Juventus</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>...</th>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17960</th>\n",
              "      <td>149662</td>\n",
              "      <td>Alan Bennett</td>\n",
              "      <td>Republic of Ireland</td>\n",
              "      <td>CB</td>\n",
              "      <td>57</td>\n",
              "      <td>38</td>\n",
              "      <td>0</td>\n",
              "      <td>57</td>\n",
              "      <td>Cork City</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17961</th>\n",
              "      <td>138083</td>\n",
              "      <td>Nicky Hunt</td>\n",
              "      <td>England</td>\n",
              "      <td>RB|CB</td>\n",
              "      <td>57</td>\n",
              "      <td>36</td>\n",
              "      <td>0</td>\n",
              "      <td>57</td>\n",
              "      <td>Crewe Alexandra</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17963</th>\n",
              "      <td>256469</td>\n",
              "      <td>Juan Camilo Suárez</td>\n",
              "      <td>Colombia</td>\n",
              "      <td>CB</td>\n",
              "      <td>56</td>\n",
              "      <td>21</td>\n",
              "      <td>0</td>\n",
              "      <td>63</td>\n",
              "      <td>Envigado FC</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17972</th>\n",
              "      <td>256150</td>\n",
              "      <td>Winston Ramírez</td>\n",
              "      <td>Colombia</td>\n",
              "      <td>RB</td>\n",
              "      <td>56</td>\n",
              "      <td>19</td>\n",
              "      <td>0</td>\n",
              "      <td>69</td>\n",
              "      <td>Cúcuta Deportivo</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17975</th>\n",
              "      <td>256101</td>\n",
              "      <td>Patrick Seagrist</td>\n",
              "      <td>United States</td>\n",
              "      <td>LB</td>\n",
              "      <td>56</td>\n",
              "      <td>22</td>\n",
              "      <td>0</td>\n",
              "      <td>66</td>\n",
              "      <td>New York Red Bulls</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "<p>4399 rows × 9 columns</p>\n",
              "</div>"
            ],
            "text/plain": [
              "       player_id                name          nationality position  overall  \\\n",
              "3         203376     Virgil van Dijk          Netherlands       CB       91   \n",
              "21        155862        Sergio Ramos                Spain       CB       89   \n",
              "25        201024   Kalidou Koulibaly              Senegal       CB       88   \n",
              "33        152729               Piqué                Spain       CB       88   \n",
              "34        138956   Giorgio Chiellini                Italy       CB       88   \n",
              "...          ...                 ...                  ...      ...      ...   \n",
              "17960     149662        Alan Bennett  Republic of Ireland       CB       57   \n",
              "17961     138083          Nicky Hunt              England    RB|CB       57   \n",
              "17963     256469  Juan Camilo Suárez             Colombia       CB       56   \n",
              "17972     256150     Winston Ramírez             Colombia       RB       56   \n",
              "17975     256101    Patrick Seagrist        United States       LB       56   \n",
              "\n",
              "       age  hits  potential                 team  \n",
              "3       29   127         92           Liverpool   \n",
              "21      34    55         89         Real Madrid   \n",
              "25      29    78         90              Napoli   \n",
              "33      33    41         88        FC Barcelona   \n",
              "34      35    19         88            Juventus   \n",
              "...    ...   ...        ...                  ...  \n",
              "17960   38     0         57           Cork City   \n",
              "17961   36     0         57     Crewe Alexandra   \n",
              "17963   21     0         63         Envigado FC   \n",
              "17972   19     0         69    Cúcuta Deportivo   \n",
              "17975   22     0         66  New York Red Bulls   \n",
              "\n",
              "[4399 rows x 9 columns]"
            ]
          },
          "execution_count": 26,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "#Dataframe containing defenders \n",
        "defenders_df"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "9iduqn5eFtOd"
      },
      "source": [
        "Let's look at the 10 defenders with highest overall rating in Fifa 21."
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 363
        },
        "id": "toQbo9LmFtOf",
        "outputId": "1d76332f-ed70-4b21-c4c7-6a020f8f9499"
      },
      "outputs": [
        {
          "data": {
            "text/html": [
              "<div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>player_id</th>\n",
              "      <th>name</th>\n",
              "      <th>nationality</th>\n",
              "      <th>position</th>\n",
              "      <th>overall</th>\n",
              "      <th>age</th>\n",
              "      <th>hits</th>\n",
              "      <th>potential</th>\n",
              "      <th>team</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>3</th>\n",
              "      <td>203376</td>\n",
              "      <td>Virgil van Dijk</td>\n",
              "      <td>Netherlands</td>\n",
              "      <td>CB</td>\n",
              "      <td>91</td>\n",
              "      <td>29</td>\n",
              "      <td>127</td>\n",
              "      <td>92</td>\n",
              "      <td>Liverpool</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>21</th>\n",
              "      <td>155862</td>\n",
              "      <td>Sergio Ramos</td>\n",
              "      <td>Spain</td>\n",
              "      <td>CB</td>\n",
              "      <td>89</td>\n",
              "      <td>34</td>\n",
              "      <td>55</td>\n",
              "      <td>89</td>\n",
              "      <td>Real Madrid</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>25</th>\n",
              "      <td>201024</td>\n",
              "      <td>Kalidou Koulibaly</td>\n",
              "      <td>Senegal</td>\n",
              "      <td>CB</td>\n",
              "      <td>88</td>\n",
              "      <td>29</td>\n",
              "      <td>78</td>\n",
              "      <td>90</td>\n",
              "      <td>Napoli</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>33</th>\n",
              "      <td>152729</td>\n",
              "      <td>Piqué</td>\n",
              "      <td>Spain</td>\n",
              "      <td>CB</td>\n",
              "      <td>88</td>\n",
              "      <td>33</td>\n",
              "      <td>41</td>\n",
              "      <td>88</td>\n",
              "      <td>FC Barcelona</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>34</th>\n",
              "      <td>138956</td>\n",
              "      <td>Giorgio Chiellini</td>\n",
              "      <td>Italy</td>\n",
              "      <td>CB</td>\n",
              "      <td>88</td>\n",
              "      <td>35</td>\n",
              "      <td>19</td>\n",
              "      <td>88</td>\n",
              "      <td>Juventus</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>37</th>\n",
              "      <td>212218</td>\n",
              "      <td>Aymeric Laporte</td>\n",
              "      <td>France</td>\n",
              "      <td>CB</td>\n",
              "      <td>87</td>\n",
              "      <td>26</td>\n",
              "      <td>38</td>\n",
              "      <td>90</td>\n",
              "      <td>Manchester City</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>49</th>\n",
              "      <td>182493</td>\n",
              "      <td>Diego Godín</td>\n",
              "      <td>Uruguay</td>\n",
              "      <td>CB</td>\n",
              "      <td>87</td>\n",
              "      <td>34</td>\n",
              "      <td>16</td>\n",
              "      <td>87</td>\n",
              "      <td>Inter</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>50</th>\n",
              "      <td>178603</td>\n",
              "      <td>Mats Hummels</td>\n",
              "      <td>Germany</td>\n",
              "      <td>CB</td>\n",
              "      <td>87</td>\n",
              "      <td>31</td>\n",
              "      <td>18</td>\n",
              "      <td>87</td>\n",
              "      <td>Borussia Dortmund</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>54</th>\n",
              "      <td>164240</td>\n",
              "      <td>Thiago Silva</td>\n",
              "      <td>Brazil</td>\n",
              "      <td>CB</td>\n",
              "      <td>87</td>\n",
              "      <td>35</td>\n",
              "      <td>28</td>\n",
              "      <td>87</td>\n",
              "      <td>Paris Saint-Germain</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>56</th>\n",
              "      <td>232363</td>\n",
              "      <td>Milan Škriniar</td>\n",
              "      <td>Slovakia</td>\n",
              "      <td>CB</td>\n",
              "      <td>86</td>\n",
              "      <td>25</td>\n",
              "      <td>62</td>\n",
              "      <td>90</td>\n",
              "      <td>Inter</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>"
            ],
            "text/plain": [
              "    player_id               name  nationality position  overall  age  hits  \\\n",
              "3      203376    Virgil van Dijk  Netherlands       CB       91   29   127   \n",
              "21     155862       Sergio Ramos        Spain       CB       89   34    55   \n",
              "25     201024  Kalidou Koulibaly      Senegal       CB       88   29    78   \n",
              "33     152729              Piqué        Spain       CB       88   33    41   \n",
              "34     138956  Giorgio Chiellini        Italy       CB       88   35    19   \n",
              "37     212218    Aymeric Laporte       France       CB       87   26    38   \n",
              "49     182493        Diego Godín      Uruguay       CB       87   34    16   \n",
              "50     178603       Mats Hummels      Germany       CB       87   31    18   \n",
              "54     164240       Thiago Silva       Brazil       CB       87   35    28   \n",
              "56     232363     Milan Škriniar     Slovakia       CB       86   25    62   \n",
              "\n",
              "    potential                  team  \n",
              "3          92            Liverpool   \n",
              "21         89          Real Madrid   \n",
              "25         90               Napoli   \n",
              "33         88         FC Barcelona   \n",
              "34         88             Juventus   \n",
              "37         90      Manchester City   \n",
              "49         87                Inter   \n",
              "50         87    Borussia Dortmund   \n",
              "54         87  Paris Saint-Germain   \n",
              "56         90                Inter   "
            ]
          },
          "execution_count": 27,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "defenders_df.head(10)"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 424
        },
        "id": "4ZFE_A5LFtOp",
        "outputId": "12d6cc1d-b20d-4b94-8687-a932aa556f38"
      },
      "outputs": [
        {
          "data": {
            "text/html": [
              "<div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>player_id</th>\n",
              "      <th>name</th>\n",
              "      <th>nationality</th>\n",
              "      <th>position</th>\n",
              "      <th>overall</th>\n",
              "      <th>age</th>\n",
              "      <th>hits</th>\n",
              "      <th>potential</th>\n",
              "      <th>team</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>4</th>\n",
              "      <td>200389</td>\n",
              "      <td>Jan Oblak</td>\n",
              "      <td>Slovenia</td>\n",
              "      <td>GK</td>\n",
              "      <td>91</td>\n",
              "      <td>27</td>\n",
              "      <td>47</td>\n",
              "      <td>93</td>\n",
              "      <td>Atlético Madrid</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>8</th>\n",
              "      <td>212831</td>\n",
              "      <td>Alisson</td>\n",
              "      <td>Brazil</td>\n",
              "      <td>GK</td>\n",
              "      <td>90</td>\n",
              "      <td>27</td>\n",
              "      <td>53</td>\n",
              "      <td>91</td>\n",
              "      <td>Liverpool</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>11</th>\n",
              "      <td>192448</td>\n",
              "      <td>Marc-André ter Stegen</td>\n",
              "      <td>Germany</td>\n",
              "      <td>GK</td>\n",
              "      <td>90</td>\n",
              "      <td>28</td>\n",
              "      <td>68</td>\n",
              "      <td>93</td>\n",
              "      <td>FC Barcelona</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>20</th>\n",
              "      <td>167495</td>\n",
              "      <td>Manuel Neuer</td>\n",
              "      <td>Germany</td>\n",
              "      <td>GK</td>\n",
              "      <td>89</td>\n",
              "      <td>34</td>\n",
              "      <td>42</td>\n",
              "      <td>89</td>\n",
              "      <td>FC Bayern München</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>22</th>\n",
              "      <td>210257</td>\n",
              "      <td>Ederson</td>\n",
              "      <td>Brazil</td>\n",
              "      <td>GK</td>\n",
              "      <td>88</td>\n",
              "      <td>26</td>\n",
              "      <td>40</td>\n",
              "      <td>91</td>\n",
              "      <td>Manchester City</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>...</th>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17955</th>\n",
              "      <td>199007</td>\n",
              "      <td>Mark McGinley</td>\n",
              "      <td>Republic of Ireland</td>\n",
              "      <td>GK</td>\n",
              "      <td>57</td>\n",
              "      <td>30</td>\n",
              "      <td>0</td>\n",
              "      <td>58</td>\n",
              "      <td>Finn Harps</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17959</th>\n",
              "      <td>175603</td>\n",
              "      <td>Rene Gilmartin</td>\n",
              "      <td>Republic of Ireland</td>\n",
              "      <td>GK</td>\n",
              "      <td>57</td>\n",
              "      <td>33</td>\n",
              "      <td>0</td>\n",
              "      <td>57</td>\n",
              "      <td>Bristol City</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17962</th>\n",
              "      <td>102881</td>\n",
              "      <td>Kyriakos Stamatopoulos</td>\n",
              "      <td>Canada</td>\n",
              "      <td>GK</td>\n",
              "      <td>57</td>\n",
              "      <td>40</td>\n",
              "      <td>1</td>\n",
              "      <td>57</td>\n",
              "      <td>AIK</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17964</th>\n",
              "      <td>256445</td>\n",
              "      <td>Ruvira</td>\n",
              "      <td>Spain</td>\n",
              "      <td>GK</td>\n",
              "      <td>56</td>\n",
              "      <td>20</td>\n",
              "      <td>0</td>\n",
              "      <td>70</td>\n",
              "      <td>CF Fuenlabrada</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17965</th>\n",
              "      <td>256436</td>\n",
              "      <td>Erland Tangvik</td>\n",
              "      <td>Norway</td>\n",
              "      <td>GK</td>\n",
              "      <td>56</td>\n",
              "      <td>23</td>\n",
              "      <td>0</td>\n",
              "      <td>63</td>\n",
              "      <td>Djurgårdens IF</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "<p>1884 rows × 9 columns</p>\n",
              "</div>"
            ],
            "text/plain": [
              "       player_id                    name          nationality position  \\\n",
              "4         200389               Jan Oblak             Slovenia       GK   \n",
              "8         212831                 Alisson               Brazil       GK   \n",
              "11        192448   Marc-André ter Stegen              Germany       GK   \n",
              "20        167495            Manuel Neuer              Germany       GK   \n",
              "22        210257                 Ederson               Brazil       GK   \n",
              "...          ...                     ...                  ...      ...   \n",
              "17955     199007           Mark McGinley  Republic of Ireland       GK   \n",
              "17959     175603          Rene Gilmartin  Republic of Ireland       GK   \n",
              "17962     102881  Kyriakos Stamatopoulos               Canada       GK   \n",
              "17964     256445                  Ruvira                Spain       GK   \n",
              "17965     256436          Erland Tangvik               Norway       GK   \n",
              "\n",
              "       overall  age  hits  potential                team  \n",
              "4           91   27    47         93    Atlético Madrid   \n",
              "8           90   27    53         91          Liverpool   \n",
              "11          90   28    68         93       FC Barcelona   \n",
              "20          89   34    42         89  FC Bayern München   \n",
              "22          88   26    40         91    Manchester City   \n",
              "...        ...  ...   ...        ...                 ...  \n",
              "17955       57   30     0         58         Finn Harps   \n",
              "17959       57   33     0         57       Bristol City   \n",
              "17962       57   40     1         57                AIK   \n",
              "17964       56   20     0         70     CF Fuenlabrada   \n",
              "17965       56   23     0         63     Djurgårdens IF   \n",
              "\n",
              "[1884 rows x 9 columns]"
            ]
          },
          "execution_count": 28,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "#Dataframe containing goal keepers\n",
        "gk_df"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "p5UuNgWXFtO8"
      },
      "source": [
        "Let's look at the 10 goalkeepers with highest overall rating in Fifa 21."
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 363
        },
        "id": "QIRnIBp1FtO-",
        "outputId": "927ab79a-3de0-405e-9ff3-c37386c32811"
      },
      "outputs": [
        {
          "data": {
            "text/html": [
              "<div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>player_id</th>\n",
              "      <th>name</th>\n",
              "      <th>nationality</th>\n",
              "      <th>position</th>\n",
              "      <th>overall</th>\n",
              "      <th>age</th>\n",
              "      <th>hits</th>\n",
              "      <th>potential</th>\n",
              "      <th>team</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>4</th>\n",
              "      <td>200389</td>\n",
              "      <td>Jan Oblak</td>\n",
              "      <td>Slovenia</td>\n",
              "      <td>GK</td>\n",
              "      <td>91</td>\n",
              "      <td>27</td>\n",
              "      <td>47</td>\n",
              "      <td>93</td>\n",
              "      <td>Atlético Madrid</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>8</th>\n",
              "      <td>212831</td>\n",
              "      <td>Alisson</td>\n",
              "      <td>Brazil</td>\n",
              "      <td>GK</td>\n",
              "      <td>90</td>\n",
              "      <td>27</td>\n",
              "      <td>53</td>\n",
              "      <td>91</td>\n",
              "      <td>Liverpool</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>11</th>\n",
              "      <td>192448</td>\n",
              "      <td>Marc-André ter Stegen</td>\n",
              "      <td>Germany</td>\n",
              "      <td>GK</td>\n",
              "      <td>90</td>\n",
              "      <td>28</td>\n",
              "      <td>68</td>\n",
              "      <td>93</td>\n",
              "      <td>FC Barcelona</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>20</th>\n",
              "      <td>167495</td>\n",
              "      <td>Manuel Neuer</td>\n",
              "      <td>Germany</td>\n",
              "      <td>GK</td>\n",
              "      <td>89</td>\n",
              "      <td>34</td>\n",
              "      <td>42</td>\n",
              "      <td>89</td>\n",
              "      <td>FC Bayern München</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>22</th>\n",
              "      <td>210257</td>\n",
              "      <td>Ederson</td>\n",
              "      <td>Brazil</td>\n",
              "      <td>GK</td>\n",
              "      <td>88</td>\n",
              "      <td>26</td>\n",
              "      <td>40</td>\n",
              "      <td>91</td>\n",
              "      <td>Manchester City</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>27</th>\n",
              "      <td>193080</td>\n",
              "      <td>De Gea</td>\n",
              "      <td>Spain</td>\n",
              "      <td>GK</td>\n",
              "      <td>88</td>\n",
              "      <td>29</td>\n",
              "      <td>39</td>\n",
              "      <td>88</td>\n",
              "      <td>Manchester United</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>28</th>\n",
              "      <td>192119</td>\n",
              "      <td>Thibaut Courtois</td>\n",
              "      <td>Belgium</td>\n",
              "      <td>GK</td>\n",
              "      <td>88</td>\n",
              "      <td>28</td>\n",
              "      <td>34</td>\n",
              "      <td>89</td>\n",
              "      <td>Real Madrid</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>32</th>\n",
              "      <td>162835</td>\n",
              "      <td>Samir Handanovic</td>\n",
              "      <td>Slovenia</td>\n",
              "      <td>GK</td>\n",
              "      <td>88</td>\n",
              "      <td>36</td>\n",
              "      <td>13</td>\n",
              "      <td>88</td>\n",
              "      <td>Inter</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>42</th>\n",
              "      <td>193041</td>\n",
              "      <td>Keylor Navas</td>\n",
              "      <td>Costa Rica</td>\n",
              "      <td>GK</td>\n",
              "      <td>87</td>\n",
              "      <td>33</td>\n",
              "      <td>28</td>\n",
              "      <td>87</td>\n",
              "      <td>Paris Saint-Germain</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>47</th>\n",
              "      <td>186153</td>\n",
              "      <td>Wojciech Szczesny</td>\n",
              "      <td>Poland</td>\n",
              "      <td>GK</td>\n",
              "      <td>87</td>\n",
              "      <td>30</td>\n",
              "      <td>17</td>\n",
              "      <td>88</td>\n",
              "      <td>Juventus</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>"
            ],
            "text/plain": [
              "    player_id                   name nationality position  overall  age  hits  \\\n",
              "4      200389              Jan Oblak    Slovenia       GK       91   27    47   \n",
              "8      212831                Alisson      Brazil       GK       90   27    53   \n",
              "11     192448  Marc-André ter Stegen     Germany       GK       90   28    68   \n",
              "20     167495           Manuel Neuer     Germany       GK       89   34    42   \n",
              "22     210257                Ederson      Brazil       GK       88   26    40   \n",
              "27     193080                 De Gea       Spain       GK       88   29    39   \n",
              "28     192119       Thibaut Courtois     Belgium       GK       88   28    34   \n",
              "32     162835       Samir Handanovic    Slovenia       GK       88   36    13   \n",
              "42     193041           Keylor Navas  Costa Rica       GK       87   33    28   \n",
              "47     186153      Wojciech Szczesny      Poland       GK       87   30    17   \n",
              "\n",
              "    potential                  team  \n",
              "4          93      Atlético Madrid   \n",
              "8          91            Liverpool   \n",
              "11         93         FC Barcelona   \n",
              "20         89    FC Bayern München   \n",
              "22         91      Manchester City   \n",
              "27         88    Manchester United   \n",
              "28         89          Real Madrid   \n",
              "32         88                Inter   \n",
              "42         87  Paris Saint-Germain   \n",
              "47         88             Juventus   "
            ]
          },
          "execution_count": 29,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "gk_df.head(10)"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "kAnS0QSpFtPH"
      },
      "source": [
        "Let's have a look at the countries from which we can find players in Fifa 21."
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 35
        },
        "id": "jdAKn0A1FtPJ",
        "outputId": "7cf227bf-ad7b-46f2-b5c4-075a7591ee1b"
      },
      "outputs": [
        {
          "data": {
            "text/plain": [
              "162"
            ]
          },
          "execution_count": 30,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "#number of different countries whose players are included in Fifa 21. \n",
        "no_of_countries = dataraw_df.nationality.nunique()\n",
        "no_of_countries"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 399
        },
        "id": "50NIG9KLFtPR",
        "outputId": "7c86e598-a522-40e1-f732-81ce01855da7"
      },
      "outputs": [
        {
          "data": {
            "text/plain": [
              "England           1496\n",
              "Germany           1138\n",
              "Spain             1055\n",
              "Argentina          970\n",
              "France             948\n",
              "Brazil             894\n",
              "Italy              637\n",
              "Colombia           561\n",
              "Japan              448\n",
              "Netherlands        418\n",
              "Uruguay            352\n",
              "Portugal           351\n",
              "Mexico             329\n",
              "Chile              318\n",
              "Austria            306\n",
              "Norway             293\n",
              "Korea Republic     286\n",
              "Poland             283\n",
              "United States      282\n",
              "Denmark            275\n",
              "Name: nationality, dtype: int64"
            ]
          },
          "execution_count": 31,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "top_countries = dataraw_df.nationality.value_counts().head(20)\n",
        "top_countries"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 469
        },
        "id": "1DlByUcIFtPZ",
        "outputId": "b1c25493-6c0e-4cc5-ab64-5fcd39f6564e"
      },
      "outputs": [
        {
          "name": "stderr",
          "output_type": "stream",
          "text": [
            "C:\\Users\\shimu\\anaconda3\\lib\\site-packages\\seaborn\\_decorators.py:36: FutureWarning: Pass the following variables as keyword args: x, y. From version 0.12, the only valid positional argument will be `data`, and passing other arguments without an explicit keyword will result in an error or misinterpretation.\n",
            "  warnings.warn(\n"
          ]
        },
        {
          "data": {
            "image/png": "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\n",
            "text/plain": [
              "<Figure size 576x432 with 1 Axes>"
            ]
          },
          "metadata": {
            "needs_background": "light"
          },
          "output_type": "display_data"
        }
      ],
      "source": [
        "#bar graph of top 20 countries with maximum number of players\n",
        "top_countries = dataraw_df.nationality.value_counts().head(20)\n",
        "plt.figure(figsize=(8,6))\n",
        "plt.xticks(rotation=75)\n",
        "plt.title(\"Top Countries\")\n",
        "sns.barplot(top_countries.index, top_countries);"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "WgtTLsU3FtPi"
      },
      "source": [
        "Now, let's have a look at the clubs from which we can find players in Fifa 21, or the clubs that are available in Fifa 21."
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 35
        },
        "id": "3X_eefMFFtPj",
        "outputId": "2217bed6-add6-4c3e-8850-cf163efd665a"
      },
      "outputs": [
        {
          "data": {
            "text/plain": [
              "713"
            ]
          },
          "execution_count": 33,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "#number of different clubs available in Fifa 21\n",
        "no_of_clubs = dataraw_df.team.nunique()\n",
        "no_of_clubs"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 944
        },
        "id": "8iLvRjmHFtPs",
        "outputId": "9a0f74a5-8596-4ead-9940-76acc3f28ab9"
      },
      "outputs": [
        {
          "data": {
            "text/plain": [
              "Free Agents                    211\n",
              "River Plate                     35\n",
              "RC Celta                        33\n",
              "Tottenham Hotspur               33\n",
              "FC Augsburg                     33\n",
              "Fortuna Düsseldorf              33\n",
              "Olympique Lyonnais              33\n",
              "Villarreal CF                   33\n",
              "Everton                         33\n",
              "Atlético Madrid                 33\n",
              "AFC Bournemouth                 33\n",
              "FC Barcelona                    33\n",
              "Valencia CF                     33\n",
              "Real Betis                      33\n",
              "Real Madrid                     33\n",
              "Liverpool                       33\n",
              "R. Valladolid CF                33\n",
              "Arsenal                         33\n",
              "Leicester City                  33\n",
              "1. FSV Mainz 05                 33\n",
              "Newcastle United                33\n",
              "RCD Espanyol                    33\n",
              "AS Monaco Football Club SA      33\n",
              "Manchester United               33\n",
              "Chelsea                         32\n",
              "D. Alavés                       32\n",
              "Watford                         32\n",
              "SC Paderborn 07                 32\n",
              "LOSC Lille                      32\n",
              "Granada CF                      32\n",
              "FC Nantes                       32\n",
              "RB Leipzig                      32\n",
              "AS Saint-Étienne                32\n",
              "Getafe CF                       32\n",
              "Levante UD                      32\n",
              "Manchester City                 32\n",
              "SV Werder Bremen                32\n",
              "Genoa                           31\n",
              "Real Sociedad                   31\n",
              "Sevilla FC                      31\n",
              "Athletic Club                   31\n",
              "Toulouse Football Club          31\n",
              "1. FC Union Berlin              31\n",
              "Stade Rennais FC                31\n",
              "Trapani                         30\n",
              "FC Emmen                        30\n",
              "Leeds United                    30\n",
              "VfL Wolfsburg                   30\n",
              "Hannover 96                     30\n",
              "VfB Stuttgart                   30\n",
              "Name: team, dtype: int64"
            ]
          },
          "execution_count": 34,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "#The clubs which has maximum number of players in Fifa 21.\n",
        "top_clubs = dataraw_df.team.value_counts().head(50)\n",
        "top_clubs"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 413
        },
        "id": "bOiWuxmSFtP2",
        "outputId": "1df732e0-8ee5-4532-ca9f-97d2ec7dae90"
      },
      "outputs": [
        {
          "data": {
            "image/png": "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\n",
            "text/plain": [
              "<Figure size 576x432 with 1 Axes>"
            ]
          },
          "metadata": {
            "needs_background": "light"
          },
          "output_type": "display_data"
        }
      ],
      "source": [
        "#bar graph of the top 30 clubs with maximum players.\n",
        "top_clubss = dataraw_df.team.value_counts().head(30)\n",
        "plt.figure(figsize=(8,6))\n",
        "plt.xticks(rotation=75)\n",
        "\n",
        "plt.bar(top_clubss.index, top_clubss);"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "Ewxwdz8zFtQW"
      },
      "source": [
        "Let's work with age category now."
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 413
        },
        "id": "uzVCM16LFtQY",
        "outputId": "36875c27-a698-4bdd-e793-f4ccc1eb0d4d"
      },
      "outputs": [
        {
          "data": {
            "image/png": "iVBORw0KGgoAAAANSUhEUgAAAfYAAAFxCAYAAACBXorcAAAAOXRFWHRTb2Z0d2FyZQBNYXRwbG90bGliIHZlcnNpb24zLjMuMywgaHR0cHM6Ly9tYXRwbG90bGliLm9yZy/Il7ecAAAACXBIWXMAAAsTAAALEwEAmpwYAAAaV0lEQVR4nO3df5BlZX3n8XcPAz24DvgjYKI1qAh+026q/DEpBxVmRgMismayZsuwLv7AIpY6SYnBiJixmLWMKVMGK5pBkB+OuFoaQMwGd3TySxgQg3ZARW++iBpw19WVUWQUu2GY3j/O6XRPe7v79O0+fXue+35VTc25z33une88dfp++jnn3OcMTUxMIEmSyrCq3wVIkqSlY7BLklQQg12SpIIY7JIkFcRglySpIAa7JEkFWd3vApbCHXfcMTE8PLyk7zk+Ps5Sv+ehyrE4mONxMMdjimNxMMdjShtj8eCDD963fv36Y2a2FxHsw8PDjIyMLOl7djqdJX/PQ5VjcTDH42COxxTH4mCOx5Q2xmJ0dPSebu0eipckqSAGuyRJBTHYJUkqiMEuSVJBDHZJkgpisEuSVBCDXZKkghjskiQVxGCXJKkgBrskSQUx2CVJKojBLklSQQx2SZIKYrBLC7Ru3Yn9LmFFcTyklaWI27ZKy+nRj17N0FC/q1g5Jib8GJFWEmfskiQVxGCXJKkgBrskSQUx2CVJKojBLklSQQx2SZIKYrBLklQQg13zcgESSTp0uLKE5uWCLAebmOh3BZI0O2fskiQVxGCXJKkgBrskSQUx2CVJKojBLklSQQx2SZIKYrBLklSQ1r7HHhEXAr8NHAFcAtwI7AQmgDuBrZl5ICIuAs4E9gPnZeZtEXFCt75t1SpJUilambFHxGbg+cALgE3AOuBiYFtmngIMAVsi4jn18xuAs4Ad9Vv8Ut826pQkqTRtHYo/Hfg6cD3wt8ANwHqqWTvALuBU4GRgd2ZOZOa9wOqIOGaWvpIkaR5tHYr/FeDJwH8Cngr8T2BVZk4uxrkPOBo4Ctg77XWT7UNd+s5qfHycTqezdNUDY2NjS/6eh6qRkZF+l6AVzp+Vip8bB3M8piznWLQV7HuBf83Mh4CMiDGqw/GT1gL3Aw/U2zPbD3Rpm9Xw8PCSh0+n0zHQpIb8Wan4uXEwx2NKG2MxOjratb2tQ/E3Ay+JiKGIeCLwH4B/qM+9A5wB7AFuAU6PiFURcRzVrP4+4PYufSVJ0jxambFn5g0RsRG4jeqXh63Ad4HLI+IIoANcm5mPRMQe4NZp/QDOn9m3jTolSSpNa193y8y3dWne1KXfdmD7jLa7uvWVJElzc4EaSZIKYrBLklQQg12SpIIY7JIkFcRglySpIAa7JEkFMdglSSqIwS5JUkEMdkmSCmKwS5JUEINdkqSCGOySJBXEYJckqSAGuyRJBTHYJUkqiMEuSVJBDHZJkgpisEuSVBCDXZKkghjskiQVxGCXJKkgBrskSQUx2CVJKojBLklSQQx2SZIKYrBLklQQg12SpIIY7JIkFcRglySpIAa7JEkFMdglSSqIwS5JUkEMdkmSCmKwS5JUEINdkqSCGOySJBXEYJckqSAGuyRJBTHYJUkqiMEuSVJBVrf1xhHxL8AD9cPvApcBfwnsB3Zn5n+PiFXAJcAzgXHg3My8OyJOmtm3rTolSSpJK8EeEWuAoczcPK3tDuB3ge8An42IZwNPBdZk5vPqMP8LYAtw6cy+mXl7G7VKklSStmbszwQeFRG7639jOzCcmd8GiIjPA6cCvwZ8DiAzvxQRvxkRR83S12CXJGkebQX7g8D7gCuAE4FdwP3Tnt8HHA8cBfx0WvsjddsDXfrOanx8nE6ns+iipxsbG1vy9zxUjYyM9LsErXD+rFT83DiY4zFlOceirWC/C7g7MyeAuyLip8Djpj2/liroH1VvT1pFFepru/Sd1fDw8JKHT6fTMdCkhvxZqfi5cTDHY0obYzE6Otq1va2r4l9Hdb6ciHgiVYD/PCKeFhFDwOnAHuAW4KV1v5OAr2fmA8BDXfpKkqR5tDVjvxLYGRE3AxNUQX8A+DhwGNWV7v8cEV8GTouILwJDwDn1698ws29LdUqSVJRWgj0zHwJe2eWpk2b0O0AV4jNf/6WZfSVJ0vxcoEaSpIIY7JIkFcRglySpIAa7JEkFMdglSSqIwS5JUkEMdkmSCmKwS5JUEINdkqSCGOySJBXEYJckqSAGuyRJBTHYJUkqiMEuSVJBDHZJkgpisEuSVBCDXZKkghjskiQVxGCXJKkgBrskSQUx2CVJKojBLklSQQx2SZIKsnq+DhHxJOBoYD9wAfDBzLyj5bokSVIPmszYPwE8AXgP8HfA+1utSJIk9axJsB8AbgIek5mfrB9LkqQVqEmwHw78OXBTRLwQOKLdkiRJUq+aBPs5wLeB9wLHAK9utSJJktSzeS+eA96cmX9Qb/91RFyN4S5J0oo0a7BHxFZgG/C4iHg5MFQ/9c3lKEySJC3crMGemTuAHRHxjsx8zzLWJEmSetTkUPwHI+IVwJrJhsy8ur2SJElSr5oE+98A3we+Vz+eaK8cSZK0GE2CfVVmnt16JZIkadGaBPvXImIDcAf1bD0zH2qzKEmS1Jsmwb4JeNm0xxPA8e2UI0mSFmPeYM/MZwJExOOBH2em59glSVqhmtzdbSNwCXAYcE1E3JOZV7ZemSRJWrAmS8q+G9gI/IDqDm9varUiSZLUs0Z3d8vMHwMTmTkG7Gu5JkmS1KMmwX53RPwZ8PiIeDtwT8s1SZKkHjW5Kv4NwLnAzcDPgN9v8sYRcSwwCpwG7Ad2Ul1RfyewNTMPRMRFwJn18+dl5m0RcUK3vgv4P0mSNLBmnbFHxMb6wrnnU9345VPA14CT5nvTiDgcuAz4Rd10MbAtM0+hupnMloh4DtVX6TYAZwE7Zuvbw/9LkqSBNNeM/Y31308DjgC+DDybata+eZ73fR9wKXBh/Xg9cGO9vQt4MZDA7vrrc/dGxOqIOGaWvtc3/P9IkjTQ5rq7238FiIjPAlsyc39EHAZ8dq43jIjXAj/KzM9HxGSwD037/vs+4GjgKGDvtJdOtnfrO6fx8XE6nc583RZkbGxsyd/zUDUyMtLvErTC+bNS8XPjYI7HlOUciybn2H9tRv9j5+n/OmAiIk4FngVcPeM1a4H7gQfq7ZntB7q0zWl4eHjJw6fT6RhoUkP+rFT83DiY4zGljbEYHR3t2t7kqvgrgW9ExHXAV4EPztU5Mzdm5qbM3Ey1vvyrgV0RsbnucgawB7gFOD0iVkXEcVQ3m7kPuL1LX0mS1ECTJWV3RMQ1VOfav1WH70KdD1weEUcAHeDazHwkIvYAt1L9grF1tr49/HuSJA2kJkvKPgt4PbCmfkxmvq7Jm9ez9kmbujy/Hdg+o+2ubn0lSdL8mpxj3wn8FfC9dkuRJEmL1STYf5CZV7ReiSRJWrQmwf5v9VKyt1OtBkdm7m61KkmS1JMmwT4MRP0HqnA32CVJWoGaXBV/TkT8BvAM4K7MvKP1qiRJUk/m/R57RPwhcDnVmvEfjoi3tl6VJEnqSZMFal4JnJKZ5wEvAH6v1YokSVLPmgT7UGbuB8jMh4GH2y1JkiT1qsnFczdHxLVUS7ueQrUUrCQBMDYGa9b0u4qVYd26E/tdgtTo4rm3RsSZwK8DV2Xm/2q/LEmHijVrYGio31WsDBMTTeZKUruaXDx3LNU90U8DXhQRj229KkmS1JMm59g/RXUzlguA7wAfa7UiSZLUs0bHjTLz0nrzqxHxihbrkSRJi9Ak2P81Iv4b8E/AemBvRDwd/v1ObJIkaYVoEuy/Xv85d1rbZVRLy76ojaIkSVJvmlwV/8LJ7YhYl5nevlWSpBVq3mCPiD8G7gceA5wTEZ/LzD9quS5JktSDJlfF/y7wUeCMzHwG8Ox2S5IkSb1qEuyPAL8K/LB+fGR75UiSpMVocvHcF+o/Z0fE+4HPtlmQJEnqXZOL5/4E+JOIeBxwQWY+1H5ZkiSpF00untsIXAIcBlwTEfdk5pWtVyZJkhasyTn2dwMbgR8A7wHe1GpFkiSpZ02C/UBm/hiYyMwxYF/LNUmSpB41Cfa7I+LPgMdHxNuBe1quSZIk9ahJsL+JKsxvBn4O/H6rFUmSpJ41+brbDZn54tYrkSRJi9Yk2H8SEb8N3AUcAO/qJknSStUk2I8F3jLtsXd1kyRphVrQ3d0kSdLK1uTiOUmSdIiYNdgj4ujlLESSJC3eXDP2zwJExIeWqRZJkrRIc51jfzgivgycGBHPrNuGqFage377pUmSpIWaK9hPBZ4EfAh4I1WoS5KkFWzWYM/MR4B7I2IL8HrgP1J9l91D85IkrVBNroq/DDgB+DvgKcAVbRYkSZJ612SBmhMzc2O9/ZmI+GKbBUmSpN41mbGviYhHAUTEkcBh7ZYkSZJ61WTG/pfAVyPiTuAZwEXtliRJknrVZEnZj0fELuB44LuZuXe+10TEYcDlQFCtLf8GYAzYWT++E9iamQci4iLgTGA/cF5m3hYRJ3Tru/D/niRJg6XRkrKZ+ePM/EqTUK+9rH7dC4BtwJ8CFwPbMvMUqq/ObYmI5wCbgA3AWcCO+vW/1LfhvytJ0kBrZa34zPwM1VfkAJ4M3A+sB26s23ZRfU/+ZGB3Zk5k5r3A6og4Zpa+kiRpHvMeio+It2bm+xb6xpm5PyI+Cvxn4L8Ap2XmRP30PuBo4Chg+lGAyfahLn1nNT4+TqfTWWiJcxobG1vy9zxUjYyM9LsE6ZDh58YUP0enLOdYNLl47qUR8f56wZoFyczXRMQFwD8DR057ai3VLP6Bentm+4EubbMaHh5e8vDpdDoGmqQF83Njip+jU9oYi9HR0a7tTQ7F/wrw/Yj4UkTc2uR77BHxqoi4sH74IFVQfyUiNtdtZwB7gFuA0yNiVUQcB6zKzPuA27v0lSRJ82gyY39ZD+/7aeAjEXETcDhwHtABLo+II+rtazPzkYjYA9xK9UvG1vr158/s20MNkiQNnCbBvh94L3AscA3wNeCeuV6QmT8HXtHlqU1d+m4Hts9ou6tbX0mSNLcmh+I/DFxFNfO+iWrBGkmStAI1CfYjM/Mfqe7DnlQLzUiSpBWoSbCPRcTpwGERcRIGuyRJK1aTYH89cA7V1fFvBd7YakWSJKlnTdaK/98R8R7g6cCdmfnd9suSJEm9mHfGHhHbgEuAFwBXRsR5bRclSZJ60+RQ/JnAxsx8C9VX0M5qtyRJktSrJsH+Q+BR9fYRwI/aK0eSJC3GrOfYI+JWqvuhHwt8KyK+CjyDg2/aIkmSVpC5Lp7zkLskSYeYWYM9M+8BiIjnUoX8mmlPv6nluiRJUg+arBX/Uaq14n/Sci2SJGmRmgT7tzJzZ9uFSJKkxWsS7NdFxCeBb042ZOa72itJkiT1qkmwbwWuA+5vtxRJkrRYTYJ9b2a+t/VKJEnSojUJ9vsi4jLgX6i+105mfrjVqiRJUk+aBPvd9d+/2mYhkiRp8ZoE+0dar0KSJC2JJsH+KapD8KuApwLfAk5usyhJktSbJvdjf97kdkQ8BvD8uiRJK1STu7tN91Pg+DYKkSRJizfvjH3aXd6GgGOAv2+7KEmS1Jsm59in3+VtLDN/2FYxkiRpcea6H/urZ2knM69uryRJktSruWbsIzMeDwHnAA8CBrskSSvQXPdjv3ByOyKeRnX71huA89ovS5Ik9aLJxXNbqcL8LZl5Q+sVSZKkns11jv1JVKvO/Rh4bmb+ZNmqkiRJPZlrxv4NYBz4R2BHRPz7E5n5ypbrkiRJPZgr2LcsWxWSJGlJzHXx3I3LWYgkSVq8hS4pK0mSVjCDXZKkghjskiQVxGCXJKkgBrskSQUx2CVJKojBLklSQQx2SZIKMu9NYBYqIg4HrgKeAgwD7wa+CewEJoA7ga2ZeSAiLgLOBPYD52XmbRFxQre+S12nJEklamPGfjawNzNPAV4C/BVwMbCtbhsCtkTEc4BNwAbgLGBH/fpf6ttCjZIkFamNYL8GeGe9PUQ1G18PTC5Ruws4FTgZ2J2ZE5l5L7A6Io6Zpa8kSWpgyQ/FZ+bPACJiLXAtsA14X2ZO1F32AUcDRwF7p710sn2oS985jY+P0+l0luY/UBsbG1vy9zxUjYyM9LsE6ZDh58YUP0enLOdYLHmwA0TEOuB64JLM/ERE/Pm0p9cC9wMP1Nsz2w90aZvT8PDwkodPp9Mx0CQtmJ8bU/wcndLGWIyOjnZtX/JD8RHxBGA3cEFmXlU33x4Rm+vtM4A9wC3A6RGxKiKOA1Zl5n2z9JUkSQ20MWN/B/BY4J0RMXmu/c3AByLiCKADXJuZj0TEHuBWql8wttZ9zwcun963hRolSSpSG+fY30wV5DNt6tJ3O7B9Rttd3fpKkqT5uUCNJEkFMdglSSqIwS5JUkEMdkmSCmKwS5JUEINdkqSCGOySJBXEYJckqSAGuyRJBTHYJUkqiMEuSVJBDHZJkgpisEuSVBCDXZKkghjskiQVxGCXJKkgBrskSQUx2CVJKojBLklSQQx2SZIKYrBLklQQg12SpIIY7JIkFcRglySpIAa7JEkFMdglSSqIwS5JUkEMdkmSCmKwS5JUEINdkqSCGOySJBXEYJckqSAGuyRJBTHYJUkqiMEuSVJBDHZJkgpisEuSVBCDXZKkghjskiQVxGCXJKkgBrskSQVZ3dYbR8QG4L2ZuTkiTgB2AhPAncDWzDwQERcBZwL7gfMy87bZ+rZVpyRJJWllxh4RbwOuANbUTRcD2zLzFGAI2BIRzwE2ARuAs4Ads/Vto0ZJkkrU1qH4bwMvn/Z4PXBjvb0LOBU4GdidmROZeS+wOiKOmaWvJElqoJVD8Zl5XUQ8ZVrTUGZO1Nv7gKOBo4C90/pMtnfrO6fx8XE6nc6i655ubGxsyd/zUDUyMtLvEqRDhp8bU/wcnbKcY9HaOfYZpp8jXwvcDzxQb89s79Z3TsPDw0sePp1Ox0CTtGB+bkzxc3RKG2MxOjratX25roq/PSI219tnAHuAW4DTI2JVRBwHrMrM+2bpK0mSGliuGfv5wOURcQTQAa7NzEciYg9wK9UvGFtn67tMNUqSdMhrLdgz89+Ak+rtu6iugJ/ZZzuwfUZb176SJGl+LlAjSVJBDHZJkgpisEuSVBCDXZKkghjskiQVxGCfxbp1J/a7BEmSFmy5vsd+yHn0o1czNNTvKlaGiYn5+0iCsTFYs2b+foPCCVJ/GOyStETWrMEJwTQTE0ZMP3goXpKkghjskiQVxGCXJKkgBrskSQUx2CVJKojBLklSQQx2SZIKYrBLklQQg12SpIIY7JIkFcRglySpIAa7JEkFMdglSSqIwS5JUkEMdkmSCmKwS5JUEINdkqSCGOySJBXEYJckqSAGuyRJBTHYJUkqiMEuSVJBDHZJkgpisEuSVBCDXZKkghjskiQVxGCXJKkgBrskSQUx2CVJKojBLklSQQx2SZIKYrBLklSQ1f0uoJuIWAVcAjwTGAfOzcy7+1uVJEkr30qdsf8OsCYznwe8HfiL/pYjSVqosbF+V7ByrFt34rL9Wytyxg6cDHwOIDO/FBG/2ed6JEkLtGYNDA31u4qVYWJi+eJ2aGJiYtn+saYi4grguszcVT++Fzg+M/d36z86Ovoj4J5lLFGSpH578vr164+Z2bhSZ+wPAGunPV41W6gDdPuPSZI0iFbqOfZbgJcCRMRJwNf7W44kSYeGlTpjvx44LSK+CAwB5/S5HkmSDgkr8hy7JEnqzUo9FC9JknpgsEuSVJCVeo592UXEBuC9mbk5Ip4N3AB8q376Q5n5qf5Vt3wi4nDgKuApwDDwbuCbwE5gArgT2JqZB/pU4rKaZTy+xwDuHxFxGHA5EFT7whuAMQZ33+g2HoczgPvGpIg4FhgFTgP2M6D7xqQZ43Eky7RvGOxARLwNeBXw87ppPXBxZg7iindnA3sz81UR8TjgjvrPtsz8QkRcCmyhusBxEHQbj3cxmPvHywAy8wURsRn4U6qLWwd13+g2Hn/LYO4bk78EXwb8om66mMHdN7qNx7LliofiK98GXj7t8XrgzIi4KSKujIi1s7yuRNcA76y3h6h+614P3Fi37QJO7UNd/TLbeAzc/pGZnwFeXz98MnA/A7xvzDEeA7dv1N4HXAp8v348sPtGrdt4LMu+YbADmXkd8PC0ptuAP87MjcB3gIv6UlgfZObPMnNfvdNdC2wDhjJz8usT+4Cj+1bgMptlPAZ5/9gfER8FPgh8nAHeN6DreAzkvhERrwV+lJmfn9Y8sPvGLOOxbPuGwd7d9Zk5OrkNPLufxSy3iFgH/BPwscz8BDD9vNhaqpnJwOgyHgO9f2Tma4CnU51fPnLaUwO3b8AvjcfuAd03Xke19sgXgGcBVwPHTnt+0PaNbuOxa7n2DYO9u89HxHPr7d+iuvhhIETEE4DdwAWZeVXdfHt9DhHgDGBPP2rrh1nGYyD3j4h4VURcWD98kOoXvq8M8L7RbTw+PYj7RmZuzMxNmbmZ6jqUVwO7BnXfmGU8/ma59g0vnuvujcAHI+Jh4AdMnUcbBO8AHgu8MyImzy2/GfhARBwBdKgOSQ+KbuPxR8D7B3D/+DTwkYi4ierq7/Oo9ofLB3Tf6DYe32NwPztmOp/B3Te6WbZcceU5SZIK4qF4SZIKYrBLklQQg12SpIIY7JIkFcRglySpIAa7pEYi4m0R8X8jYk2/a5E0O4NdUlNnA58Ezup3IZJm5wI1kuZVryD2baqbWvwPYGe9itYOqnXA/x8wlpmvjYg/BF5JdbvOT2bmB/pTtTSYnLFLauJc4IrMTGA8IjZQhfxrM/NFVKFPRDwD+D3gZOAU4HciIvpUszSQDHZJc4qIxwIvBd4cEZ+jukvXHwBPzMxv1N0m1wH/DapbmP5D/efxwInLW7E02Ax2SfM5G7gyM1+cmS8BNgAvBn5Rz9ABTqr/TuAbwAvrG2DsBL62vOVKg81glzSfc4GPTT7IzAeB66hC+6qI+HvgucDDmflVqpn6zRHxFarZ+v9Z9oqlAeZNYCT1JCK2An+dmT+KiHcDD2Xmu/pdlzTovCpeUq9+COyOiJ8BPwVe0+d6JOGMXZKkoniOXZKkghjskiQVxGCXJKkgBrskSQUx2CVJKojBLklSQf4/u77LR3dm6x8AAAAASUVORK5CYII=\n",
            "text/plain": [
              "<Figure size 576x432 with 1 Axes>"
            ]
          },
          "metadata": {
            "needs_background": "light"
          },
          "output_type": "display_data"
        }
      ],
      "source": [
        "#histogram depicting number of players in different age groups\n",
        "plt.figure(figsize=(8, 6))\n",
        "\n",
        "plt.xlabel('Age')\n",
        "plt.ylabel('Number of respondents')\n",
        "\n",
        "plt.hist(dataraw_df.age, bins=np.arange(15,50,5), color='blue');"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "knqJMpl3FtQd"
      },
      "source": [
        "Let's group the players of the top 3 age categories. So that we can find the top 5 players in each of the top 3 age categories."
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 424
        },
        "id": "YO3M_HujFtQf",
        "outputId": "8b0225d3-acdb-4f8e-fce7-cb55c6570a21"
      },
      "outputs": [
        {
          "data": {
            "text/html": [
              "<div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>player_id</th>\n",
              "      <th>name</th>\n",
              "      <th>nationality</th>\n",
              "      <th>position</th>\n",
              "      <th>overall</th>\n",
              "      <th>age</th>\n",
              "      <th>hits</th>\n",
              "      <th>potential</th>\n",
              "      <th>team</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>13</th>\n",
              "      <td>231747</td>\n",
              "      <td>Kylian Mbappé</td>\n",
              "      <td>France</td>\n",
              "      <td>ST|RW|LW</td>\n",
              "      <td>89</td>\n",
              "      <td>21</td>\n",
              "      <td>222</td>\n",
              "      <td>95</td>\n",
              "      <td>Paris Saint-Germain</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>23</th>\n",
              "      <td>202652</td>\n",
              "      <td>Raheem Sterling</td>\n",
              "      <td>England</td>\n",
              "      <td>RW|LW</td>\n",
              "      <td>88</td>\n",
              "      <td>25</td>\n",
              "      <td>61</td>\n",
              "      <td>90</td>\n",
              "      <td>Manchester City</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>35</th>\n",
              "      <td>218667</td>\n",
              "      <td>Bernardo Silva</td>\n",
              "      <td>Portugal</td>\n",
              "      <td>CM|CAM|RW</td>\n",
              "      <td>87</td>\n",
              "      <td>25</td>\n",
              "      <td>53</td>\n",
              "      <td>90</td>\n",
              "      <td>Manchester City</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>36</th>\n",
              "      <td>212622</td>\n",
              "      <td>Joshua Kimmich</td>\n",
              "      <td>Germany</td>\n",
              "      <td>RB|CDM|CM</td>\n",
              "      <td>87</td>\n",
              "      <td>25</td>\n",
              "      <td>82</td>\n",
              "      <td>90</td>\n",
              "      <td>FC Bayern München</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>56</th>\n",
              "      <td>232363</td>\n",
              "      <td>Milan Škriniar</td>\n",
              "      <td>Slovakia</td>\n",
              "      <td>CB</td>\n",
              "      <td>86</td>\n",
              "      <td>25</td>\n",
              "      <td>62</td>\n",
              "      <td>90</td>\n",
              "      <td>Inter</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>...</th>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17966</th>\n",
              "      <td>256417</td>\n",
              "      <td>Mads Sande</td>\n",
              "      <td>Norway</td>\n",
              "      <td>CM</td>\n",
              "      <td>56</td>\n",
              "      <td>22</td>\n",
              "      <td>0</td>\n",
              "      <td>63</td>\n",
              "      <td>FK Haugesund</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17975</th>\n",
              "      <td>256101</td>\n",
              "      <td>Patrick Seagrist</td>\n",
              "      <td>United States</td>\n",
              "      <td>LB</td>\n",
              "      <td>56</td>\n",
              "      <td>22</td>\n",
              "      <td>0</td>\n",
              "      <td>66</td>\n",
              "      <td>New York Red Bulls</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17976</th>\n",
              "      <td>256093</td>\n",
              "      <td>Jaime Ortíz</td>\n",
              "      <td>Ecuador</td>\n",
              "      <td>ST</td>\n",
              "      <td>56</td>\n",
              "      <td>21</td>\n",
              "      <td>0</td>\n",
              "      <td>64</td>\n",
              "      <td>Sociedad Deportiva Aucas</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17977</th>\n",
              "      <td>256088</td>\n",
              "      <td>Michael Carcelén</td>\n",
              "      <td>Ecuador</td>\n",
              "      <td>CM</td>\n",
              "      <td>56</td>\n",
              "      <td>23</td>\n",
              "      <td>0</td>\n",
              "      <td>64</td>\n",
              "      <td>Club Deportivo El Nacional</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17979</th>\n",
              "      <td>256073</td>\n",
              "      <td>Sergio Sulbarán</td>\n",
              "      <td>Venezuela</td>\n",
              "      <td>RW</td>\n",
              "      <td>56</td>\n",
              "      <td>22</td>\n",
              "      <td>0</td>\n",
              "      <td>62</td>\n",
              "      <td>Zamora Fútbol Club</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "<p>6567 rows × 9 columns</p>\n",
              "</div>"
            ],
            "text/plain": [
              "       player_id              name    nationality   position  overall  age  \\\n",
              "13        231747     Kylian Mbappé         France   ST|RW|LW       89   21   \n",
              "23        202652   Raheem Sterling        England      RW|LW       88   25   \n",
              "35        218667    Bernardo Silva       Portugal  CM|CAM|RW       87   25   \n",
              "36        212622    Joshua Kimmich        Germany  RB|CDM|CM       87   25   \n",
              "56        232363    Milan Škriniar       Slovakia         CB       86   25   \n",
              "...          ...               ...            ...        ...      ...  ...   \n",
              "17966     256417        Mads Sande         Norway         CM       56   22   \n",
              "17975     256101  Patrick Seagrist  United States         LB       56   22   \n",
              "17976     256093       Jaime Ortíz        Ecuador         ST       56   21   \n",
              "17977     256088  Michael Carcelén        Ecuador         CM       56   23   \n",
              "17979     256073   Sergio Sulbarán      Venezuela         RW       56   22   \n",
              "\n",
              "       hits  potential                         team  \n",
              "13      222         95         Paris Saint-Germain   \n",
              "23       61         90             Manchester City   \n",
              "35       53         90             Manchester City   \n",
              "36       82         90           FC Bayern München   \n",
              "56       62         90                       Inter   \n",
              "...     ...        ...                          ...  \n",
              "17966     0         63                FK Haugesund   \n",
              "17975     0         66          New York Red Bulls   \n",
              "17976     0         64    Sociedad Deportiva Aucas   \n",
              "17977     0         64  Club Deportivo El Nacional   \n",
              "17979     0         62          Zamora Fútbol Club   \n",
              "\n",
              "[6567 rows x 9 columns]"
            ]
          },
          "execution_count": 37,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "#players of age 21 to 25\n",
        "age2125_df = dataraw_df[ (dataraw_df.age == 21) | \n",
        "                         (dataraw_df.age == 22) | \n",
        "                         (dataraw_df.age == 23) |\n",
        "                         (dataraw_df.age == 24) |\n",
        "                         (dataraw_df.age == 25)\n",
        "                         \n",
        "                        ]\n",
        "age2125_df"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 424
        },
        "id": "fywnRSPXFtQk",
        "outputId": "867d3b2a-c45b-434e-9436-b15376359738"
      },
      "outputs": [
        {
          "data": {
            "text/html": [
              "<div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>player_id</th>\n",
              "      <th>name</th>\n",
              "      <th>nationality</th>\n",
              "      <th>position</th>\n",
              "      <th>overall</th>\n",
              "      <th>age</th>\n",
              "      <th>hits</th>\n",
              "      <th>potential</th>\n",
              "      <th>team</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>2</th>\n",
              "      <td>190871</td>\n",
              "      <td>Neymar Jr</td>\n",
              "      <td>Brazil</td>\n",
              "      <td>CAM|LW</td>\n",
              "      <td>92</td>\n",
              "      <td>28</td>\n",
              "      <td>186</td>\n",
              "      <td>92</td>\n",
              "      <td>Paris Saint-Germain</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>3</th>\n",
              "      <td>203376</td>\n",
              "      <td>Virgil van Dijk</td>\n",
              "      <td>Netherlands</td>\n",
              "      <td>CB</td>\n",
              "      <td>91</td>\n",
              "      <td>29</td>\n",
              "      <td>127</td>\n",
              "      <td>92</td>\n",
              "      <td>Liverpool</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>4</th>\n",
              "      <td>200389</td>\n",
              "      <td>Jan Oblak</td>\n",
              "      <td>Slovenia</td>\n",
              "      <td>GK</td>\n",
              "      <td>91</td>\n",
              "      <td>27</td>\n",
              "      <td>47</td>\n",
              "      <td>93</td>\n",
              "      <td>Atlético Madrid</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>5</th>\n",
              "      <td>192985</td>\n",
              "      <td>Kevin De Bruyne</td>\n",
              "      <td>Belgium</td>\n",
              "      <td>CM|CAM</td>\n",
              "      <td>91</td>\n",
              "      <td>29</td>\n",
              "      <td>119</td>\n",
              "      <td>91</td>\n",
              "      <td>Manchester City</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>7</th>\n",
              "      <td>183277</td>\n",
              "      <td>Eden Hazard</td>\n",
              "      <td>Belgium</td>\n",
              "      <td>ST|LW</td>\n",
              "      <td>91</td>\n",
              "      <td>29</td>\n",
              "      <td>66</td>\n",
              "      <td>91</td>\n",
              "      <td>Real Madrid</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>...</th>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17954</th>\n",
              "      <td>203372</td>\n",
              "      <td>Alex Cooper</td>\n",
              "      <td>Scotland</td>\n",
              "      <td>LB|LM|CM</td>\n",
              "      <td>57</td>\n",
              "      <td>28</td>\n",
              "      <td>0</td>\n",
              "      <td>57</td>\n",
              "      <td>Sligo Rovers</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17955</th>\n",
              "      <td>199007</td>\n",
              "      <td>Mark McGinley</td>\n",
              "      <td>Republic of Ireland</td>\n",
              "      <td>GK</td>\n",
              "      <td>57</td>\n",
              "      <td>30</td>\n",
              "      <td>0</td>\n",
              "      <td>58</td>\n",
              "      <td>Finn Harps</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17956</th>\n",
              "      <td>198487</td>\n",
              "      <td>Luka Mijaljevic</td>\n",
              "      <td>Sweden</td>\n",
              "      <td>ST</td>\n",
              "      <td>57</td>\n",
              "      <td>29</td>\n",
              "      <td>0</td>\n",
              "      <td>57</td>\n",
              "      <td>AFC Eskilstuna</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17957</th>\n",
              "      <td>198485</td>\n",
              "      <td>Shane McEleney</td>\n",
              "      <td>Republic of Ireland</td>\n",
              "      <td>CB</td>\n",
              "      <td>57</td>\n",
              "      <td>29</td>\n",
              "      <td>0</td>\n",
              "      <td>58</td>\n",
              "      <td>Finn Harps</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17967</th>\n",
              "      <td>256329</td>\n",
              "      <td>Hassan Al Shamrani</td>\n",
              "      <td>Saudi Arabia</td>\n",
              "      <td>CB|CDM</td>\n",
              "      <td>56</td>\n",
              "      <td>29</td>\n",
              "      <td>0</td>\n",
              "      <td>57</td>\n",
              "      <td>Damac FC</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "<p>6170 rows × 9 columns</p>\n",
              "</div>"
            ],
            "text/plain": [
              "       player_id                name          nationality  position  overall  \\\n",
              "2         190871           Neymar Jr               Brazil    CAM|LW       92   \n",
              "3         203376     Virgil van Dijk          Netherlands        CB       91   \n",
              "4         200389           Jan Oblak             Slovenia        GK       91   \n",
              "5         192985     Kevin De Bruyne              Belgium    CM|CAM       91   \n",
              "7         183277         Eden Hazard              Belgium     ST|LW       91   \n",
              "...          ...                 ...                  ...       ...      ...   \n",
              "17954     203372         Alex Cooper             Scotland  LB|LM|CM       57   \n",
              "17955     199007       Mark McGinley  Republic of Ireland        GK       57   \n",
              "17956     198487     Luka Mijaljevic               Sweden        ST       57   \n",
              "17957     198485      Shane McEleney  Republic of Ireland        CB       57   \n",
              "17967     256329  Hassan Al Shamrani         Saudi Arabia    CB|CDM       56   \n",
              "\n",
              "       age  hits  potential                  team  \n",
              "2       28   186         92  Paris Saint-Germain   \n",
              "3       29   127         92            Liverpool   \n",
              "4       27    47         93      Atlético Madrid   \n",
              "5       29   119         91      Manchester City   \n",
              "7       29    66         91          Real Madrid   \n",
              "...    ...   ...        ...                   ...  \n",
              "17954   28     0         57         Sligo Rovers   \n",
              "17955   30     0         58           Finn Harps   \n",
              "17956   29     0         57       AFC Eskilstuna   \n",
              "17957   29     0         58           Finn Harps   \n",
              "17967   29     0         57             Damac FC   \n",
              "\n",
              "[6170 rows x 9 columns]"
            ]
          },
          "execution_count": 38,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "#players of age 26 to 30 \n",
        "age2630_df = dataraw_df[(dataraw_df.age == 26) | \n",
        "                         (dataraw_df.age == 27) | \n",
        "                         (dataraw_df.age == 28) | \n",
        "                         (dataraw_df.age == 29) |\n",
        "                         (dataraw_df.age == 30) \n",
        "                         \n",
        "                        ]\n",
        "age2630_df"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 424
        },
        "id": "NnQAtfFMFtQm",
        "outputId": "3043af42-aa72-48b6-bb9f-272701d87934"
      },
      "outputs": [
        {
          "data": {
            "text/html": [
              "<div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>player_id</th>\n",
              "      <th>name</th>\n",
              "      <th>nationality</th>\n",
              "      <th>position</th>\n",
              "      <th>overall</th>\n",
              "      <th>age</th>\n",
              "      <th>hits</th>\n",
              "      <th>potential</th>\n",
              "      <th>team</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>0</th>\n",
              "      <td>158023</td>\n",
              "      <td>Lionel Messi</td>\n",
              "      <td>Argentina</td>\n",
              "      <td>ST|CF|RW</td>\n",
              "      <td>94</td>\n",
              "      <td>33</td>\n",
              "      <td>299</td>\n",
              "      <td>94</td>\n",
              "      <td>FC Barcelona</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>1</th>\n",
              "      <td>20801</td>\n",
              "      <td>Cristiano Ronaldo</td>\n",
              "      <td>Portugal</td>\n",
              "      <td>ST|LW</td>\n",
              "      <td>93</td>\n",
              "      <td>35</td>\n",
              "      <td>276</td>\n",
              "      <td>93</td>\n",
              "      <td>Juventus</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>6</th>\n",
              "      <td>188545</td>\n",
              "      <td>Robert Lewandowski</td>\n",
              "      <td>Poland</td>\n",
              "      <td>ST</td>\n",
              "      <td>91</td>\n",
              "      <td>31</td>\n",
              "      <td>89</td>\n",
              "      <td>91</td>\n",
              "      <td>FC Bayern München</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>12</th>\n",
              "      <td>153079</td>\n",
              "      <td>Sergio Agüero</td>\n",
              "      <td>Argentina</td>\n",
              "      <td>ST</td>\n",
              "      <td>90</td>\n",
              "      <td>32</td>\n",
              "      <td>50</td>\n",
              "      <td>90</td>\n",
              "      <td>Manchester City</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>18</th>\n",
              "      <td>177003</td>\n",
              "      <td>Luka Modric</td>\n",
              "      <td>Croatia</td>\n",
              "      <td>CM</td>\n",
              "      <td>89</td>\n",
              "      <td>34</td>\n",
              "      <td>31</td>\n",
              "      <td>89</td>\n",
              "      <td>Real Madrid</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>...</th>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "      <td>...</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17928</th>\n",
              "      <td>224670</td>\n",
              "      <td>Qiao Wei</td>\n",
              "      <td>China PR</td>\n",
              "      <td>CB</td>\n",
              "      <td>57</td>\n",
              "      <td>33</td>\n",
              "      <td>0</td>\n",
              "      <td>57</td>\n",
              "      <td>Shenzen FC</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17930</th>\n",
              "      <td>224628</td>\n",
              "      <td>Wang Dalong</td>\n",
              "      <td>China PR</td>\n",
              "      <td>CB</td>\n",
              "      <td>57</td>\n",
              "      <td>31</td>\n",
              "      <td>0</td>\n",
              "      <td>57</td>\n",
              "      <td>Shenzen FC</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17942</th>\n",
              "      <td>222182</td>\n",
              "      <td>Zhu Xiaogang</td>\n",
              "      <td>China PR</td>\n",
              "      <td>CDM|CM</td>\n",
              "      <td>57</td>\n",
              "      <td>32</td>\n",
              "      <td>0</td>\n",
              "      <td>57</td>\n",
              "      <td>Dalian YiFang FC</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17958</th>\n",
              "      <td>182352</td>\n",
              "      <td>Li Benjian</td>\n",
              "      <td>China PR</td>\n",
              "      <td>LM|CM|CAM</td>\n",
              "      <td>57</td>\n",
              "      <td>34</td>\n",
              "      <td>1</td>\n",
              "      <td>57</td>\n",
              "      <td>Henan Jianye FC</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17959</th>\n",
              "      <td>175603</td>\n",
              "      <td>Rene Gilmartin</td>\n",
              "      <td>Republic of Ireland</td>\n",
              "      <td>GK</td>\n",
              "      <td>57</td>\n",
              "      <td>33</td>\n",
              "      <td>0</td>\n",
              "      <td>57</td>\n",
              "      <td>Bristol City</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "<p>2996 rows × 9 columns</p>\n",
              "</div>"
            ],
            "text/plain": [
              "       player_id                name          nationality   position  overall  \\\n",
              "0         158023        Lionel Messi            Argentina   ST|CF|RW       94   \n",
              "1          20801   Cristiano Ronaldo             Portugal      ST|LW       93   \n",
              "6         188545  Robert Lewandowski               Poland         ST       91   \n",
              "12        153079       Sergio Agüero            Argentina         ST       90   \n",
              "18        177003         Luka Modric              Croatia         CM       89   \n",
              "...          ...                 ...                  ...        ...      ...   \n",
              "17928     224670            Qiao Wei             China PR         CB       57   \n",
              "17930     224628         Wang Dalong             China PR         CB       57   \n",
              "17942     222182        Zhu Xiaogang             China PR     CDM|CM       57   \n",
              "17958     182352          Li Benjian             China PR  LM|CM|CAM       57   \n",
              "17959     175603      Rene Gilmartin  Republic of Ireland         GK       57   \n",
              "\n",
              "       age  hits  potential                team  \n",
              "0       33   299         94       FC Barcelona   \n",
              "1       35   276         93           Juventus   \n",
              "6       31    89         91  FC Bayern München   \n",
              "12      32    50         90    Manchester City   \n",
              "18      34    31         89        Real Madrid   \n",
              "...    ...   ...        ...                 ...  \n",
              "17928   33     0         57         Shenzen FC   \n",
              "17930   31     0         57         Shenzen FC   \n",
              "17942   32     0         57   Dalian YiFang FC   \n",
              "17958   34     1         57    Henan Jianye FC   \n",
              "17959   33     0         57       Bristol City   \n",
              "\n",
              "[2996 rows x 9 columns]"
            ]
          },
          "execution_count": 39,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "#players of age 31 to 36\n",
        "age3135_df = dataraw_df[(dataraw_df.age == 31) | \n",
        "                         (dataraw_df.age == 32) | \n",
        "                         (dataraw_df.age == 33) | \n",
        "                         (dataraw_df.age == 34) |\n",
        "                         (dataraw_df.age == 35) \n",
        "                         \n",
        "                        ]\n",
        "age3135_df"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "0gcd1rVxFtQp",
        "outputId": "962d2bf6-0d10-4c1d-ffcc-81cc4a49deb4"
      },
      "outputs": [
        {
          "data": {
            "image/png": "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\n",
            "text/plain": [
              "<Figure size 432x288 with 1 Axes>"
            ]
          },
          "metadata": {
            "needs_background": "light"
          },
          "output_type": "display_data"
        }
      ],
      "source": [
        "#countplot denoting the number of players in each age  \n",
        "sns.countplot(x=dataraw_df.age)\n",
        "plt.xticks(rotation=90);\n"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "UZhn1VT8FtQs",
        "outputId": "88b4d314-4611-4ff5-a96a-b28e12f7a1ba"
      },
      "outputs": [
        {
          "name": "stderr",
          "output_type": "stream",
          "text": [
            "C:\\Users\\shimu\\anaconda3\\lib\\site-packages\\seaborn\\_decorators.py:36: FutureWarning: Pass the following variables as keyword args: x, y. From version 0.12, the only valid positional argument will be `data`, and passing other arguments without an explicit keyword will result in an error or misinterpretation.\n",
            "  warnings.warn(\n"
          ]
        },
        {
          "data": {
            "image/png": "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\n",
            "text/plain": [
              "<Figure size 720x576 with 1 Axes>"
            ]
          },
          "metadata": {
            "needs_background": "light"
          },
          "output_type": "display_data"
        }
      ],
      "source": [
        "#Scatterplot of overall vs age \n",
        "plt.figure(figsize=(10,8))\n",
        "plt.title('Age vs Overall Rating')\n",
        "\n",
        "sns.scatterplot(dataraw_df.age, dataraw_df.overall);\n",
        "\n"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "ZoLPhvkfFtQx"
      },
      "source": [
        "###### From the scatterplot we can observe many things like : \n",
        "1. There are no players under age 20 who have a rating of more than 80. \n",
        "2. Players with 90 + rating are in the age goup of 27 to 35. \n",
        "3. Between age 20 to 40 and rating 55 to 85 there is an almost same overall distribution of players."
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "QMLjUA-qFtQy"
      },
      "outputs": [],
      "source": [
        "import jovian"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "wQjIO1IfFtQ7",
        "outputId": "41a90d8f-b995-4d98-f796-44ae6c66cfa5"
      },
      "outputs": [
        {
          "data": {
            "application/javascript": [
              "window.require && require([\"base/js/namespace\"],function(Jupyter){Jupyter.notebook.save_checkpoint()})"
            ],
            "text/plain": [
              "<IPython.core.display.Javascript object>"
            ]
          },
          "metadata": {},
          "output_type": "display_data"
        },
        {
          "name": "stdout",
          "output_type": "stream",
          "text": [
            "[jovian] Attempting to save notebook..\n",
            "[jovian] Updating notebook \"sayakpm3/fifa-21-players-data-analysis-in-python1\" on https://jovian.ml/\n",
            "[jovian] Uploading notebook..\n",
            "[jovian] Capturing environment..\n",
            "[jovian] Committed successfully! https://jovian.ml/sayakpm3/fifa-21-players-data-analysis-in-python1\n"
          ]
        },
        {
          "data": {
            "text/plain": [
              "'https://jovian.ml/sayakpm3/fifa-21-players-data-analysis-in-python1'"
            ]
          },
          "execution_count": 43,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "jovian.commit()"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "U_oUWvieFtQ-"
      },
      "source": [
        "## Asking and Answering Questions\n",
        "\n",
        "Let's ask some specific questions related to Fifa 21, and try to answer them using data frame operations and interesting visualizations."
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "oXT4S_pZFtQ_"
      },
      "source": [
        "### Q: Who are the top 10 players with the highest overall rating in Fifa 21 ?"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "4CHjmziyFtRA"
      },
      "source": [
        "The original dataset is sorted in descending order of overall rating, so to find the top 10 players with highest overall rating we don't require to sort the dataset again and simply use the .head() method to find the top 10 players."
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "k_ZFgUGDFtRC",
        "outputId": "33eba22e-d040-48d5-8c2f-f49f8b5f134b"
      },
      "outputs": [
        {
          "data": {
            "text/html": [
              "<div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>name</th>\n",
              "      <th>age</th>\n",
              "      <th>overall</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>0</th>\n",
              "      <td>Lionel Messi</td>\n",
              "      <td>33</td>\n",
              "      <td>94</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>1</th>\n",
              "      <td>Cristiano Ronaldo</td>\n",
              "      <td>35</td>\n",
              "      <td>93</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>2</th>\n",
              "      <td>Neymar Jr</td>\n",
              "      <td>28</td>\n",
              "      <td>92</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>3</th>\n",
              "      <td>Virgil van Dijk</td>\n",
              "      <td>29</td>\n",
              "      <td>91</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>4</th>\n",
              "      <td>Jan Oblak</td>\n",
              "      <td>27</td>\n",
              "      <td>91</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>5</th>\n",
              "      <td>Kevin De Bruyne</td>\n",
              "      <td>29</td>\n",
              "      <td>91</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>6</th>\n",
              "      <td>Robert Lewandowski</td>\n",
              "      <td>31</td>\n",
              "      <td>91</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>7</th>\n",
              "      <td>Eden Hazard</td>\n",
              "      <td>29</td>\n",
              "      <td>91</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>8</th>\n",
              "      <td>Alisson</td>\n",
              "      <td>27</td>\n",
              "      <td>90</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>9</th>\n",
              "      <td>Mohamed Salah</td>\n",
              "      <td>28</td>\n",
              "      <td>90</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>"
            ],
            "text/plain": [
              "                 name  age  overall\n",
              "0        Lionel Messi   33       94\n",
              "1   Cristiano Ronaldo   35       93\n",
              "2           Neymar Jr   28       92\n",
              "3     Virgil van Dijk   29       91\n",
              "4           Jan Oblak   27       91\n",
              "5     Kevin De Bruyne   29       91\n",
              "6  Robert Lewandowski   31       91\n",
              "7         Eden Hazard   29       91\n",
              "8             Alisson   27       90\n",
              "9       Mohamed Salah   28       90"
            ]
          },
          "execution_count": 44,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "top10_df = dataraw_df[['name', 'age', 'overall']]\n",
        "top10_df.head(10)"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "ZgChST5xFtRF"
      },
      "source": [
        "There we go according to the overall rating Lionel Messi is at the top with a of 94 rating and Mohamed Salah is 10th with a rating of 90 in Fifa 21."
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "0vqHYz3yFtRG"
      },
      "source": [
        "### Q: Who are the top 5 players having the highest rating in each category (forwards, midfielders, defenders, goalkeepers) in Fifa 21 ?"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "agVnkbQBFtRH"
      },
      "source": [
        "We will use the already created dataframes like forwards_df & midfielders_df, alongwith .head() method to get the top 10 players of each category."
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "uojuohkFFtRH"
      },
      "source": [
        "###### Forwards"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "G9fas5uMFtRK",
        "scrolled": true,
        "outputId": "1d8c59e1-f702-421c-bf9d-4a629af8ebf9"
      },
      "outputs": [
        {
          "data": {
            "text/html": [
              "<div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>name</th>\n",
              "      <th>age</th>\n",
              "      <th>overall</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>0</th>\n",
              "      <td>Lionel Messi</td>\n",
              "      <td>33</td>\n",
              "      <td>94</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>1</th>\n",
              "      <td>Cristiano Ronaldo</td>\n",
              "      <td>35</td>\n",
              "      <td>93</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>2</th>\n",
              "      <td>Neymar Jr</td>\n",
              "      <td>28</td>\n",
              "      <td>92</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>6</th>\n",
              "      <td>Robert Lewandowski</td>\n",
              "      <td>31</td>\n",
              "      <td>91</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>7</th>\n",
              "      <td>Eden Hazard</td>\n",
              "      <td>29</td>\n",
              "      <td>91</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>9</th>\n",
              "      <td>Mohamed Salah</td>\n",
              "      <td>28</td>\n",
              "      <td>90</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>10</th>\n",
              "      <td>Sadio Mané</td>\n",
              "      <td>28</td>\n",
              "      <td>90</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>12</th>\n",
              "      <td>Sergio Agüero</td>\n",
              "      <td>32</td>\n",
              "      <td>90</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>13</th>\n",
              "      <td>Kylian Mbappé</td>\n",
              "      <td>21</td>\n",
              "      <td>89</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>15</th>\n",
              "      <td>Harry Kane</td>\n",
              "      <td>27</td>\n",
              "      <td>89</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>"
            ],
            "text/plain": [
              "                  name  age  overall\n",
              "0         Lionel Messi   33       94\n",
              "1    Cristiano Ronaldo   35       93\n",
              "2            Neymar Jr   28       92\n",
              "6   Robert Lewandowski   31       91\n",
              "7          Eden Hazard   29       91\n",
              "9        Mohamed Salah   28       90\n",
              "10          Sadio Mané   28       90\n",
              "12       Sergio Agüero   32       90\n",
              "13       Kylian Mbappé   21       89\n",
              "15          Harry Kane   27       89"
            ]
          },
          "execution_count": 45,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "top10forward_df = forwards_df[['name', 'age', 'overall']]\n",
        "top10forward_df.head(10)"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "VDHze16_FtRQ"
      },
      "source": [
        "From the above dataframe we can observe that, 'Lionel Messi' is ranked as the best forward, followed by 'Cristiano Ronaldo' and 'Neymar Jr' as the 2nd and 3rd best respectively, while 'Harry Kane' is ranked as the 10th best among the forwards in Fifa 21."
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "wuQVIS2pFtRS"
      },
      "source": [
        "###### Midfielders"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "JWzGo8NBFtRS",
        "outputId": "719b0e4c-cd96-4522-9264-2e6f5149f83d"
      },
      "outputs": [
        {
          "data": {
            "text/html": [
              "<div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>name</th>\n",
              "      <th>age</th>\n",
              "      <th>overall</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>5</th>\n",
              "      <td>Kevin De Bruyne</td>\n",
              "      <td>29</td>\n",
              "      <td>91</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>14</th>\n",
              "      <td>N'Golo Kanté</td>\n",
              "      <td>29</td>\n",
              "      <td>89</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17</th>\n",
              "      <td>Toni Kroos</td>\n",
              "      <td>30</td>\n",
              "      <td>89</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>18</th>\n",
              "      <td>Luka Modric</td>\n",
              "      <td>34</td>\n",
              "      <td>89</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>26</th>\n",
              "      <td>Casemiro</td>\n",
              "      <td>28</td>\n",
              "      <td>88</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>29</th>\n",
              "      <td>Sergio Busquets</td>\n",
              "      <td>32</td>\n",
              "      <td>88</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>40</th>\n",
              "      <td>Marco Verratti</td>\n",
              "      <td>27</td>\n",
              "      <td>87</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>41</th>\n",
              "      <td>Paul Pogba</td>\n",
              "      <td>27</td>\n",
              "      <td>87</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>44</th>\n",
              "      <td>Christian Eriksen</td>\n",
              "      <td>28</td>\n",
              "      <td>87</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>45</th>\n",
              "      <td>Parejo</td>\n",
              "      <td>31</td>\n",
              "      <td>87</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>"
            ],
            "text/plain": [
              "                 name  age  overall\n",
              "5     Kevin De Bruyne   29       91\n",
              "14       N'Golo Kanté   29       89\n",
              "17         Toni Kroos   30       89\n",
              "18        Luka Modric   34       89\n",
              "26           Casemiro   28       88\n",
              "29    Sergio Busquets   32       88\n",
              "40     Marco Verratti   27       87\n",
              "41         Paul Pogba   27       87\n",
              "44  Christian Eriksen   28       87\n",
              "45             Parejo   31       87"
            ]
          },
          "execution_count": 46,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "top10midfielders_df = midfielders_df[['name', 'age', 'overall']]\n",
        "top10midfielders_df.head(10)"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "qkGx05iyFtRW"
      },
      "source": [
        "From the above dataframe we can observe that, 'Kevin De Bruyne' is ranked as the best midfielder, followed by 'N'Golo Kanté' and 'Toni Kroos' as the 2nd and 3rd best respectively, while 'Parejo' is ranked as the 10th best among the midfielders in Fifa 21."
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "XpUZ19A4FtRW"
      },
      "source": [
        "###### Defenders"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "Z5yY7NaGFtRX",
        "outputId": "91b80d89-1148-48dc-81c9-a9facd0ee6e9"
      },
      "outputs": [
        {
          "data": {
            "text/html": [
              "<div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>name</th>\n",
              "      <th>age</th>\n",
              "      <th>overall</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>3</th>\n",
              "      <td>Virgil van Dijk</td>\n",
              "      <td>29</td>\n",
              "      <td>91</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>21</th>\n",
              "      <td>Sergio Ramos</td>\n",
              "      <td>34</td>\n",
              "      <td>89</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>25</th>\n",
              "      <td>Kalidou Koulibaly</td>\n",
              "      <td>29</td>\n",
              "      <td>88</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>33</th>\n",
              "      <td>Piqué</td>\n",
              "      <td>33</td>\n",
              "      <td>88</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>34</th>\n",
              "      <td>Giorgio Chiellini</td>\n",
              "      <td>35</td>\n",
              "      <td>88</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>37</th>\n",
              "      <td>Aymeric Laporte</td>\n",
              "      <td>26</td>\n",
              "      <td>87</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>49</th>\n",
              "      <td>Diego Godín</td>\n",
              "      <td>34</td>\n",
              "      <td>87</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>50</th>\n",
              "      <td>Mats Hummels</td>\n",
              "      <td>31</td>\n",
              "      <td>87</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>54</th>\n",
              "      <td>Thiago Silva</td>\n",
              "      <td>35</td>\n",
              "      <td>87</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>56</th>\n",
              "      <td>Milan Škriniar</td>\n",
              "      <td>25</td>\n",
              "      <td>86</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>"
            ],
            "text/plain": [
              "                 name  age  overall\n",
              "3     Virgil van Dijk   29       91\n",
              "21       Sergio Ramos   34       89\n",
              "25  Kalidou Koulibaly   29       88\n",
              "33              Piqué   33       88\n",
              "34  Giorgio Chiellini   35       88\n",
              "37    Aymeric Laporte   26       87\n",
              "49        Diego Godín   34       87\n",
              "50       Mats Hummels   31       87\n",
              "54       Thiago Silva   35       87\n",
              "56     Milan Škriniar   25       86"
            ]
          },
          "execution_count": 47,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "top10defenders_df = defenders_df[['name', 'age', 'overall']]\n",
        "top10defenders_df.head(10)"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "6E3QwyWVFtRa"
      },
      "source": [
        "From the above dataframe we can observe that, 'Virgil van Dijk' is ranked as the best defender, followed by 'Sergio Ramos' and 'Kalidou Koulibaly' as the 2nd and 3rd best respectively, while 'Milan Škriniar' is ranked as the 10th best among the defenders in Fifa 21."
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "7ZeHK20dFtRa"
      },
      "source": [
        "###### Goalkeepers"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "ImiLz5vmFtRb",
        "outputId": "32135d66-b82f-49ad-bc6a-4c527b37bc36"
      },
      "outputs": [
        {
          "data": {
            "text/html": [
              "<div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>name</th>\n",
              "      <th>age</th>\n",
              "      <th>overall</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>4</th>\n",
              "      <td>Jan Oblak</td>\n",
              "      <td>27</td>\n",
              "      <td>91</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>8</th>\n",
              "      <td>Alisson</td>\n",
              "      <td>27</td>\n",
              "      <td>90</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>11</th>\n",
              "      <td>Marc-André ter Stegen</td>\n",
              "      <td>28</td>\n",
              "      <td>90</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>20</th>\n",
              "      <td>Manuel Neuer</td>\n",
              "      <td>34</td>\n",
              "      <td>89</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>22</th>\n",
              "      <td>Ederson</td>\n",
              "      <td>26</td>\n",
              "      <td>88</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>27</th>\n",
              "      <td>De Gea</td>\n",
              "      <td>29</td>\n",
              "      <td>88</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>28</th>\n",
              "      <td>Thibaut Courtois</td>\n",
              "      <td>28</td>\n",
              "      <td>88</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>32</th>\n",
              "      <td>Samir Handanovic</td>\n",
              "      <td>36</td>\n",
              "      <td>88</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>42</th>\n",
              "      <td>Keylor Navas</td>\n",
              "      <td>33</td>\n",
              "      <td>87</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>47</th>\n",
              "      <td>Wojciech Szczesny</td>\n",
              "      <td>30</td>\n",
              "      <td>87</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>"
            ],
            "text/plain": [
              "                     name  age  overall\n",
              "4               Jan Oblak   27       91\n",
              "8                 Alisson   27       90\n",
              "11  Marc-André ter Stegen   28       90\n",
              "20           Manuel Neuer   34       89\n",
              "22                Ederson   26       88\n",
              "27                 De Gea   29       88\n",
              "28       Thibaut Courtois   28       88\n",
              "32       Samir Handanovic   36       88\n",
              "42           Keylor Navas   33       87\n",
              "47      Wojciech Szczesny   30       87"
            ]
          },
          "execution_count": 48,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "top10gks_df = gk_df[['name', 'age', 'overall']]\n",
        "top10gks_df.head(10)"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "_kusrm-YFtRi"
      },
      "source": [
        "From the above dataframe we can observe that, 'Jan Oblak' is ranked as the best goalkeeper, followed by 'Alisson' and 'Marc-André ter Stegen' as the 2nd and 3rd best respectively, while 'Wojciech Szczesny' is ranked as the 10th best among the goalkeepers in Fifa 21."
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "Xcy35mAmFtRi"
      },
      "source": [
        "### Q: What is the total number of different countries from which Fifa 21 players are selected ? Which are the top 10 countries to have most number of players in Fifa 21 ? "
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "s1Z42FS8FtRj"
      },
      "source": [
        "To find the number of different countries we will use the method .nunique(). For finding top 10 countries with highest player participation in Fifa 21 we will use the method .value_counts(). We will use a bar graph for better visualisation."
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "ht5AV2SSFtRj",
        "outputId": "51d177ac-c847-4849-ba6d-d8b5cc74c283"
      },
      "outputs": [
        {
          "data": {
            "text/plain": [
              "162"
            ]
          },
          "execution_count": 49,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "no_of_countries = dataraw_df.nationality.nunique()\n",
        "no_of_countries"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "q5ekCzaYFtRp"
      },
      "source": [
        "So, we can see that there are a total of 162 different countries from which we can find players in Fifa 21. "
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "9uhmtkISFtRq",
        "outputId": "e13c535d-618e-48c2-9647-52360e921f06"
      },
      "outputs": [
        {
          "data": {
            "text/plain": [
              "England        1496\n",
              "Germany        1138\n",
              "Spain          1055\n",
              "Argentina       970\n",
              "France          948\n",
              "Brazil          894\n",
              "Italy           637\n",
              "Colombia        561\n",
              "Japan           448\n",
              "Netherlands     418\n",
              "Name: nationality, dtype: int64"
            ]
          },
          "execution_count": 50,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "top_countries = dataraw_df.nationality.value_counts().head(10)\n",
        "top_countries"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "wTu7O0HpFtRt",
        "outputId": "b39f7651-6d6f-4361-aa4b-164066c963d4"
      },
      "outputs": [
        {
          "name": "stderr",
          "output_type": "stream",
          "text": [
            "C:\\Users\\shimu\\anaconda3\\lib\\site-packages\\seaborn\\_decorators.py:36: FutureWarning: Pass the following variables as keyword args: x, y. From version 0.12, the only valid positional argument will be `data`, and passing other arguments without an explicit keyword will result in an error or misinterpretation.\n",
            "  warnings.warn(\n"
          ]
        },
        {
          "data": {
            "image/png": "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\n",
            "text/plain": [
              "<Figure size 864x720 with 1 Axes>"
            ]
          },
          "metadata": {
            "needs_background": "light"
          },
          "output_type": "display_data"
        }
      ],
      "source": [
        "top_countries = dataraw_df.nationality.value_counts().head(15)\n",
        "plt.figure(figsize=(12,10))\n",
        "plt.xticks(rotation=75)\n",
        "plt.title(\"Top Countries\")\n",
        "sns.barplot(top_countries.index, top_countries);"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "PPcSudhFFtRx"
      },
      "source": [
        "From the above graph we can see that England is the country with highest number of players in Fifa 21, followed by Germany and Spain."
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "wXEx14BmFtRz"
      },
      "source": [
        "Now, we can also check if there is any player from our country in Fifa 21.\n",
        "So, I am an Indian. I will be checking if any player of India is there in Fifa 21. And if there is Indian players present in Fifa 21, we will also find out who they are."
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "JnOTwMYLFtR0",
        "outputId": "d8c17848-bbe5-47fe-ccce-a10bcb9a6d74"
      },
      "outputs": [
        {
          "name": "stdout",
          "output_type": "stream",
          "text": [
            "Indian Players are there in Fifa 21.\n"
          ]
        }
      ],
      "source": [
        "for a in dataraw_df.nationality:\n",
        "    if a == 'India':\n",
        "        print(\"Indian Players are there in Fifa 21.\")\n",
        "        break\n",
        "\n",
        "else: \n",
        "    print(\"Indian Players are not included in Fifa 21.\")\n",
        "\n",
        "    "
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "PmPWr57iFtR3"
      },
      "source": [
        "So, we found that Indian Players are present in Fifa 21. Now, we can find out who are the players."
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "Tge7_by9FtR3",
        "outputId": "0dbd7d73-4c25-45b2-82c4-175c2aae0173"
      },
      "outputs": [
        {
          "data": {
            "text/html": [
              "<div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>player_id</th>\n",
              "      <th>name</th>\n",
              "      <th>nationality</th>\n",
              "      <th>position</th>\n",
              "      <th>overall</th>\n",
              "      <th>age</th>\n",
              "      <th>hits</th>\n",
              "      <th>potential</th>\n",
              "      <th>team</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>11885</th>\n",
              "      <td>251742</td>\n",
              "      <td>Gajodara Chatterjee</td>\n",
              "      <td>India</td>\n",
              "      <td>GK</td>\n",
              "      <td>64</td>\n",
              "      <td>35</td>\n",
              "      <td>1</td>\n",
              "      <td>64</td>\n",
              "      <td>Free Agents</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>13068</th>\n",
              "      <td>251728</td>\n",
              "      <td>Bhadrashree Raj</td>\n",
              "      <td>India</td>\n",
              "      <td>RB</td>\n",
              "      <td>63</td>\n",
              "      <td>32</td>\n",
              "      <td>1</td>\n",
              "      <td>63</td>\n",
              "      <td>Free Agents</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>13069</th>\n",
              "      <td>251723</td>\n",
              "      <td>Prakul Bhatt</td>\n",
              "      <td>India</td>\n",
              "      <td>ST</td>\n",
              "      <td>63</td>\n",
              "      <td>35</td>\n",
              "      <td>3</td>\n",
              "      <td>63</td>\n",
              "      <td>Free Agents</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>14135</th>\n",
              "      <td>251736</td>\n",
              "      <td>Anvit Swaminathan</td>\n",
              "      <td>India</td>\n",
              "      <td>LM|CAM</td>\n",
              "      <td>62</td>\n",
              "      <td>28</td>\n",
              "      <td>2</td>\n",
              "      <td>62</td>\n",
              "      <td>Free Agents</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>14136</th>\n",
              "      <td>251727</td>\n",
              "      <td>Hantidev Bhandari</td>\n",
              "      <td>India</td>\n",
              "      <td>RM|LM</td>\n",
              "      <td>62</td>\n",
              "      <td>31</td>\n",
              "      <td>0</td>\n",
              "      <td>62</td>\n",
              "      <td>Free Agents</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>14137</th>\n",
              "      <td>251722</td>\n",
              "      <td>Abhimoda Chakraborty</td>\n",
              "      <td>India</td>\n",
              "      <td>CB</td>\n",
              "      <td>62</td>\n",
              "      <td>34</td>\n",
              "      <td>0</td>\n",
              "      <td>62</td>\n",
              "      <td>Free Agents</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>15058</th>\n",
              "      <td>251729</td>\n",
              "      <td>Devindra Pillai</td>\n",
              "      <td>India</td>\n",
              "      <td>RM|RW</td>\n",
              "      <td>61</td>\n",
              "      <td>32</td>\n",
              "      <td>0</td>\n",
              "      <td>61</td>\n",
              "      <td>Free Agents</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>15824</th>\n",
              "      <td>251747</td>\n",
              "      <td>Anuvinda Khurana</td>\n",
              "      <td>India</td>\n",
              "      <td>CB</td>\n",
              "      <td>60</td>\n",
              "      <td>27</td>\n",
              "      <td>2</td>\n",
              "      <td>62</td>\n",
              "      <td>Free Agents</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>15825</th>\n",
              "      <td>251743</td>\n",
              "      <td>Adit Ginti</td>\n",
              "      <td>India</td>\n",
              "      <td>LB|LM</td>\n",
              "      <td>60</td>\n",
              "      <td>26</td>\n",
              "      <td>3</td>\n",
              "      <td>62</td>\n",
              "      <td>Free Agents</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>15826</th>\n",
              "      <td>251732</td>\n",
              "      <td>Remil Nadkarni</td>\n",
              "      <td>India</td>\n",
              "      <td>CAM|CF</td>\n",
              "      <td>60</td>\n",
              "      <td>34</td>\n",
              "      <td>1</td>\n",
              "      <td>60</td>\n",
              "      <td>Free Agents</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>15827</th>\n",
              "      <td>251731</td>\n",
              "      <td>Bismeet Sidhu</td>\n",
              "      <td>India</td>\n",
              "      <td>CDM|CM</td>\n",
              "      <td>60</td>\n",
              "      <td>32</td>\n",
              "      <td>2</td>\n",
              "      <td>60</td>\n",
              "      <td>Free Agents</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>15828</th>\n",
              "      <td>251725</td>\n",
              "      <td>Tapish Atwal</td>\n",
              "      <td>India</td>\n",
              "      <td>CB</td>\n",
              "      <td>60</td>\n",
              "      <td>36</td>\n",
              "      <td>0</td>\n",
              "      <td>60</td>\n",
              "      <td>Free Agents</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>15829</th>\n",
              "      <td>251721</td>\n",
              "      <td>Attana Deshpande</td>\n",
              "      <td>India</td>\n",
              "      <td>LM</td>\n",
              "      <td>60</td>\n",
              "      <td>39</td>\n",
              "      <td>0</td>\n",
              "      <td>60</td>\n",
              "      <td>Free Agents</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>16566</th>\n",
              "      <td>251748</td>\n",
              "      <td>Dinkerrai Bajwa</td>\n",
              "      <td>India</td>\n",
              "      <td>CB|CDM</td>\n",
              "      <td>59</td>\n",
              "      <td>39</td>\n",
              "      <td>2</td>\n",
              "      <td>59</td>\n",
              "      <td>Free Agents</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>16567</th>\n",
              "      <td>251746</td>\n",
              "      <td>Randhir Jayaraman</td>\n",
              "      <td>India</td>\n",
              "      <td>ST</td>\n",
              "      <td>59</td>\n",
              "      <td>35</td>\n",
              "      <td>0</td>\n",
              "      <td>59</td>\n",
              "      <td>Free Agents</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>16568</th>\n",
              "      <td>251740</td>\n",
              "      <td>Gunjeevan Thakkar</td>\n",
              "      <td>India</td>\n",
              "      <td>ST</td>\n",
              "      <td>59</td>\n",
              "      <td>23</td>\n",
              "      <td>10</td>\n",
              "      <td>61</td>\n",
              "      <td>Free Agents</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>16569</th>\n",
              "      <td>251739</td>\n",
              "      <td>Vihaan Boral</td>\n",
              "      <td>India</td>\n",
              "      <td>GK</td>\n",
              "      <td>59</td>\n",
              "      <td>31</td>\n",
              "      <td>2</td>\n",
              "      <td>60</td>\n",
              "      <td>Free Agents</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>16570</th>\n",
              "      <td>251726</td>\n",
              "      <td>Diasha Sundaram</td>\n",
              "      <td>India</td>\n",
              "      <td>CB</td>\n",
              "      <td>59</td>\n",
              "      <td>31</td>\n",
              "      <td>0</td>\n",
              "      <td>59</td>\n",
              "      <td>Free Agents</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17127</th>\n",
              "      <td>251749</td>\n",
              "      <td>Omesh Patla</td>\n",
              "      <td>India</td>\n",
              "      <td>CAM</td>\n",
              "      <td>58</td>\n",
              "      <td>27</td>\n",
              "      <td>3</td>\n",
              "      <td>59</td>\n",
              "      <td>Free Agents</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17128</th>\n",
              "      <td>251745</td>\n",
              "      <td>Chapal Palan</td>\n",
              "      <td>India</td>\n",
              "      <td>CM</td>\n",
              "      <td>58</td>\n",
              "      <td>29</td>\n",
              "      <td>1</td>\n",
              "      <td>58</td>\n",
              "      <td>Free Agents</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17129</th>\n",
              "      <td>251735</td>\n",
              "      <td>Amanpreet Varkay</td>\n",
              "      <td>India</td>\n",
              "      <td>LB</td>\n",
              "      <td>58</td>\n",
              "      <td>34</td>\n",
              "      <td>1</td>\n",
              "      <td>58</td>\n",
              "      <td>Free Agents</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17130</th>\n",
              "      <td>251733</td>\n",
              "      <td>Palkesh Nagarajan</td>\n",
              "      <td>India</td>\n",
              "      <td>GK</td>\n",
              "      <td>58</td>\n",
              "      <td>30</td>\n",
              "      <td>0</td>\n",
              "      <td>59</td>\n",
              "      <td>Free Agents</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17131</th>\n",
              "      <td>251730</td>\n",
              "      <td>Durvish Raghavan</td>\n",
              "      <td>India</td>\n",
              "      <td>ST</td>\n",
              "      <td>58</td>\n",
              "      <td>26</td>\n",
              "      <td>1</td>\n",
              "      <td>61</td>\n",
              "      <td>Free Agents</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17132</th>\n",
              "      <td>251724</td>\n",
              "      <td>Taranjot Agarwal</td>\n",
              "      <td>India</td>\n",
              "      <td>LB|LM</td>\n",
              "      <td>58</td>\n",
              "      <td>34</td>\n",
              "      <td>0</td>\n",
              "      <td>58</td>\n",
              "      <td>Free Agents</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>17656</th>\n",
              "      <td>251750</td>\n",
              "      <td>Dhwanil Singhal</td>\n",
              "      <td>India</td>\n",
              "      <td>CDM</td>\n",
              "      <td>57</td>\n",
              "      <td>35</td>\n",
              "      <td>0</td>\n",
              "      <td>57</td>\n",
              "      <td>Free Agents</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>"
            ],
            "text/plain": [
              "       player_id                  name nationality position  overall  age  \\\n",
              "11885     251742   Gajodara Chatterjee       India       GK       64   35   \n",
              "13068     251728       Bhadrashree Raj       India       RB       63   32   \n",
              "13069     251723          Prakul Bhatt       India       ST       63   35   \n",
              "14135     251736     Anvit Swaminathan       India   LM|CAM       62   28   \n",
              "14136     251727     Hantidev Bhandari       India    RM|LM       62   31   \n",
              "14137     251722  Abhimoda Chakraborty       India       CB       62   34   \n",
              "15058     251729       Devindra Pillai       India    RM|RW       61   32   \n",
              "15824     251747      Anuvinda Khurana       India       CB       60   27   \n",
              "15825     251743            Adit Ginti       India    LB|LM       60   26   \n",
              "15826     251732        Remil Nadkarni       India   CAM|CF       60   34   \n",
              "15827     251731         Bismeet Sidhu       India   CDM|CM       60   32   \n",
              "15828     251725          Tapish Atwal       India       CB       60   36   \n",
              "15829     251721      Attana Deshpande       India       LM       60   39   \n",
              "16566     251748       Dinkerrai Bajwa       India   CB|CDM       59   39   \n",
              "16567     251746     Randhir Jayaraman       India       ST       59   35   \n",
              "16568     251740     Gunjeevan Thakkar       India       ST       59   23   \n",
              "16569     251739          Vihaan Boral       India       GK       59   31   \n",
              "16570     251726       Diasha Sundaram       India       CB       59   31   \n",
              "17127     251749           Omesh Patla       India      CAM       58   27   \n",
              "17128     251745          Chapal Palan       India       CM       58   29   \n",
              "17129     251735      Amanpreet Varkay       India       LB       58   34   \n",
              "17130     251733     Palkesh Nagarajan       India       GK       58   30   \n",
              "17131     251730      Durvish Raghavan       India       ST       58   26   \n",
              "17132     251724      Taranjot Agarwal       India    LB|LM       58   34   \n",
              "17656     251750       Dhwanil Singhal       India      CDM       57   35   \n",
              "\n",
              "       hits  potential          team  \n",
              "11885     1         64  Free Agents   \n",
              "13068     1         63  Free Agents   \n",
              "13069     3         63  Free Agents   \n",
              "14135     2         62  Free Agents   \n",
              "14136     0         62  Free Agents   \n",
              "14137     0         62  Free Agents   \n",
              "15058     0         61  Free Agents   \n",
              "15824     2         62  Free Agents   \n",
              "15825     3         62  Free Agents   \n",
              "15826     1         60  Free Agents   \n",
              "15827     2         60  Free Agents   \n",
              "15828     0         60  Free Agents   \n",
              "15829     0         60  Free Agents   \n",
              "16566     2         59  Free Agents   \n",
              "16567     0         59  Free Agents   \n",
              "16568    10         61  Free Agents   \n",
              "16569     2         60  Free Agents   \n",
              "16570     0         59  Free Agents   \n",
              "17127     3         59  Free Agents   \n",
              "17128     1         58  Free Agents   \n",
              "17129     1         58  Free Agents   \n",
              "17130     0         59  Free Agents   \n",
              "17131     1         61  Free Agents   \n",
              "17132     0         58  Free Agents   \n",
              "17656     0         57  Free Agents   "
            ]
          },
          "execution_count": 53,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "indian_df = dataraw_df[(dataraw_df.nationality == 'India') ]\n",
        "indian_df"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "IBUKoRx3FtR5",
        "outputId": "ce234456-446a-48da-ca8d-6975a35fad2c"
      },
      "outputs": [
        {
          "data": {
            "text/plain": [
              "25"
            ]
          },
          "execution_count": 54,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "indian_df.name.count()"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "A13xJx0JFtR7"
      },
      "source": [
        "So, we can see that there are 25 Indian Players in Fifa 21 and all of them are Free Agents, that is they do not represent any club."
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "goDsE930FtR9"
      },
      "source": [
        "### Q: What is the total number of different clubs from which Fifa 21 players are selected ? Which are the top 10 clubs to have most number of players in Fifa 21 ? "
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "4_zXM48AFtR9"
      },
      "source": [
        "To find the number of different clubs present in Fifa 21 we will use the .nunique() method once again.\n",
        "For finding the clubs having maximum player we will use the .value_counts method. For better visualistaion we will also plot a bar graph."
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "O_5RzE2mFtR9",
        "outputId": "3ee04dea-91f1-4b38-9ac4-2ca85c2915de"
      },
      "outputs": [
        {
          "data": {
            "text/plain": [
              "713"
            ]
          },
          "execution_count": 55,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "no_of_clubs = dataraw_df.team.nunique()\n",
        "no_of_clubs"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "UG1jWy4xFtSA",
        "outputId": "cf308603-9bf9-485b-ce64-f1bf396d05eb"
      },
      "outputs": [
        {
          "data": {
            "text/plain": [
              "Free Agents                    211\n",
              "River Plate                     35\n",
              "RC Celta                        33\n",
              "Tottenham Hotspur               33\n",
              "FC Augsburg                     33\n",
              "Fortuna Düsseldorf              33\n",
              "Olympique Lyonnais              33\n",
              "Villarreal CF                   33\n",
              "Everton                         33\n",
              "Atlético Madrid                 33\n",
              "AFC Bournemouth                 33\n",
              "FC Barcelona                    33\n",
              "Valencia CF                     33\n",
              "Real Betis                      33\n",
              "Real Madrid                     33\n",
              "Liverpool                       33\n",
              "R. Valladolid CF                33\n",
              "Arsenal                         33\n",
              "Leicester City                  33\n",
              "1. FSV Mainz 05                 33\n",
              "Newcastle United                33\n",
              "RCD Espanyol                    33\n",
              "AS Monaco Football Club SA      33\n",
              "Manchester United               33\n",
              "Chelsea                         32\n",
              "D. Alavés                       32\n",
              "Watford                         32\n",
              "SC Paderborn 07                 32\n",
              "LOSC Lille                      32\n",
              "Granada CF                      32\n",
              "FC Nantes                       32\n",
              "RB Leipzig                      32\n",
              "AS Saint-Étienne                32\n",
              "Getafe CF                       32\n",
              "Levante UD                      32\n",
              "Manchester City                 32\n",
              "SV Werder Bremen                32\n",
              "Genoa                           31\n",
              "Real Sociedad                   31\n",
              "Sevilla FC                      31\n",
              "Athletic Club                   31\n",
              "Toulouse Football Club          31\n",
              "1. FC Union Berlin              31\n",
              "Stade Rennais FC                31\n",
              "Trapani                         30\n",
              "FC Emmen                        30\n",
              "Leeds United                    30\n",
              "VfL Wolfsburg                   30\n",
              "Hannover 96                     30\n",
              "VfB Stuttgart                   30\n",
              "Name: team, dtype: int64"
            ]
          },
          "execution_count": 56,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "top_clubs = dataraw_df.team.value_counts().head(50)\n",
        "top_clubs"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "gpDYmIqDFtSB",
        "outputId": "41790937-7ad4-4b8b-b00a-48bb84c3a30a"
      },
      "outputs": [
        {
          "data": {
            "image/png": "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\n",
            "text/plain": [
              "<Figure size 864x720 with 1 Axes>"
            ]
          },
          "metadata": {
            "needs_background": "light"
          },
          "output_type": "display_data"
        }
      ],
      "source": [
        "top_clubss = dataraw_df.team.value_counts().head(30)\n",
        "plt.figure(figsize=(12,10))\n",
        "plt.xticks(rotation=75)\n",
        "\n",
        "plt.bar(top_clubss.index, top_clubss);"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "cD4eCOdsFtSH"
      },
      "source": [
        "So, there are 713 different clubs in Fifa 21. There are 211 Free Agents in Fifa 21. Rest of the players represents a club and in the top 50 category we can see that most of the clubs has on an average 32 players in their teams. From the bar graph also we can visualise that all the teams other than the Free Agents have more or less the same bars. Although River Plate is the team with highest number of players that is 35"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "wStMxLjpFtSI"
      },
      "source": [
        "### Q: What are the age groups with maximum number of players in Fifa 21?"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "T8DjIWGsFtSI"
      },
      "source": [
        "We will plot a histogram depicting the number of players in different age groups. From the histogram we will be get to know which are the age groups with maximum players. "
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "D4qDBFZSFtSJ",
        "outputId": "9eacd181-4205-4aa8-bfb9-11e48cb6af23"
      },
      "outputs": [
        {
          "data": {
            "image/png": "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\n",
            "text/plain": [
              "<Figure size 864x720 with 1 Axes>"
            ]
          },
          "metadata": {
            "needs_background": "light"
          },
          "output_type": "display_data"
        }
      ],
      "source": [
        "plt.figure(figsize=(12, 10))\n",
        "\n",
        "plt.xlabel('Age')\n",
        "plt.ylabel('Number of respondents')\n",
        "\n",
        "plt.hist(dataraw_df.age, bins=np.arange(15,50,5), color='pink');"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "7j3iUxDKFtSO"
      },
      "source": [
        "The maximum number of players falls in the age group 25 to 30, followed by 20 to 25 and 30 to 35."
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "auqKaXOSFtSP"
      },
      "source": [
        "### Q: Who are the top 5 players in age groups with maximum players? "
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "aQb44dC-FtSQ"
      },
      "source": [
        "So, we need to find the top 5 players in the age groups 21-25, 26-30, 31-35. To find the top 10 players we have to use the dataframes containing the players of different age groups and the .head() method."
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "X_C1HaT5FtSR"
      },
      "source": [
        "###### Age Group 21 to 25."
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "apfDn9uiFtSR",
        "outputId": "ba06797e-2dfb-4b74-d520-68940478dd46"
      },
      "outputs": [
        {
          "data": {
            "text/html": [
              "<div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>player_id</th>\n",
              "      <th>name</th>\n",
              "      <th>nationality</th>\n",
              "      <th>position</th>\n",
              "      <th>overall</th>\n",
              "      <th>age</th>\n",
              "      <th>hits</th>\n",
              "      <th>potential</th>\n",
              "      <th>team</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>13</th>\n",
              "      <td>231747</td>\n",
              "      <td>Kylian Mbappé</td>\n",
              "      <td>France</td>\n",
              "      <td>ST|RW|LW</td>\n",
              "      <td>89</td>\n",
              "      <td>21</td>\n",
              "      <td>222</td>\n",
              "      <td>95</td>\n",
              "      <td>Paris Saint-Germain</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>23</th>\n",
              "      <td>202652</td>\n",
              "      <td>Raheem Sterling</td>\n",
              "      <td>England</td>\n",
              "      <td>RW|LW</td>\n",
              "      <td>88</td>\n",
              "      <td>25</td>\n",
              "      <td>61</td>\n",
              "      <td>90</td>\n",
              "      <td>Manchester City</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>35</th>\n",
              "      <td>218667</td>\n",
              "      <td>Bernardo Silva</td>\n",
              "      <td>Portugal</td>\n",
              "      <td>CM|CAM|RW</td>\n",
              "      <td>87</td>\n",
              "      <td>25</td>\n",
              "      <td>53</td>\n",
              "      <td>90</td>\n",
              "      <td>Manchester City</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>36</th>\n",
              "      <td>212622</td>\n",
              "      <td>Joshua Kimmich</td>\n",
              "      <td>Germany</td>\n",
              "      <td>RB|CDM|CM</td>\n",
              "      <td>87</td>\n",
              "      <td>25</td>\n",
              "      <td>82</td>\n",
              "      <td>90</td>\n",
              "      <td>FC Bayern München</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>56</th>\n",
              "      <td>232363</td>\n",
              "      <td>Milan Škriniar</td>\n",
              "      <td>Slovakia</td>\n",
              "      <td>CB</td>\n",
              "      <td>86</td>\n",
              "      <td>25</td>\n",
              "      <td>62</td>\n",
              "      <td>90</td>\n",
              "      <td>Inter</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>"
            ],
            "text/plain": [
              "    player_id             name nationality   position  overall  age  hits  \\\n",
              "13     231747    Kylian Mbappé      France   ST|RW|LW       89   21   222   \n",
              "23     202652  Raheem Sterling     England      RW|LW       88   25    61   \n",
              "35     218667   Bernardo Silva    Portugal  CM|CAM|RW       87   25    53   \n",
              "36     212622   Joshua Kimmich     Germany  RB|CDM|CM       87   25    82   \n",
              "56     232363   Milan Škriniar    Slovakia         CB       86   25    62   \n",
              "\n",
              "    potential                  team  \n",
              "13         95  Paris Saint-Germain   \n",
              "23         90      Manchester City   \n",
              "35         90      Manchester City   \n",
              "36         90    FC Bayern München   \n",
              "56         90                Inter   "
            ]
          },
          "execution_count": 59,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "age2125_df.head(5)"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "tGcai6w0FtSY"
      },
      "source": [
        "From the above dataframe we can observe that in the age group 21 to 25, 'Kylian Mbappé' is ranked 1st, followed by 'Raheem Sterling' and 'Bernardo Silva'."
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "Kyvp67X3FtSZ"
      },
      "source": [
        "###### Age Group 26 to 30."
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "vF4EbLWlFtSa",
        "outputId": "57bb69b9-70fe-446b-8dd3-f0ec32148685"
      },
      "outputs": [
        {
          "data": {
            "text/html": [
              "<div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>player_id</th>\n",
              "      <th>name</th>\n",
              "      <th>nationality</th>\n",
              "      <th>position</th>\n",
              "      <th>overall</th>\n",
              "      <th>age</th>\n",
              "      <th>hits</th>\n",
              "      <th>potential</th>\n",
              "      <th>team</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>2</th>\n",
              "      <td>190871</td>\n",
              "      <td>Neymar Jr</td>\n",
              "      <td>Brazil</td>\n",
              "      <td>CAM|LW</td>\n",
              "      <td>92</td>\n",
              "      <td>28</td>\n",
              "      <td>186</td>\n",
              "      <td>92</td>\n",
              "      <td>Paris Saint-Germain</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>3</th>\n",
              "      <td>203376</td>\n",
              "      <td>Virgil van Dijk</td>\n",
              "      <td>Netherlands</td>\n",
              "      <td>CB</td>\n",
              "      <td>91</td>\n",
              "      <td>29</td>\n",
              "      <td>127</td>\n",
              "      <td>92</td>\n",
              "      <td>Liverpool</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>4</th>\n",
              "      <td>200389</td>\n",
              "      <td>Jan Oblak</td>\n",
              "      <td>Slovenia</td>\n",
              "      <td>GK</td>\n",
              "      <td>91</td>\n",
              "      <td>27</td>\n",
              "      <td>47</td>\n",
              "      <td>93</td>\n",
              "      <td>Atlético Madrid</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>5</th>\n",
              "      <td>192985</td>\n",
              "      <td>Kevin De Bruyne</td>\n",
              "      <td>Belgium</td>\n",
              "      <td>CM|CAM</td>\n",
              "      <td>91</td>\n",
              "      <td>29</td>\n",
              "      <td>119</td>\n",
              "      <td>91</td>\n",
              "      <td>Manchester City</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>7</th>\n",
              "      <td>183277</td>\n",
              "      <td>Eden Hazard</td>\n",
              "      <td>Belgium</td>\n",
              "      <td>ST|LW</td>\n",
              "      <td>91</td>\n",
              "      <td>29</td>\n",
              "      <td>66</td>\n",
              "      <td>91</td>\n",
              "      <td>Real Madrid</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>"
            ],
            "text/plain": [
              "   player_id             name  nationality position  overall  age  hits  \\\n",
              "2     190871        Neymar Jr       Brazil   CAM|LW       92   28   186   \n",
              "3     203376  Virgil van Dijk  Netherlands       CB       91   29   127   \n",
              "4     200389        Jan Oblak     Slovenia       GK       91   27    47   \n",
              "5     192985  Kevin De Bruyne      Belgium   CM|CAM       91   29   119   \n",
              "7     183277      Eden Hazard      Belgium    ST|LW       91   29    66   \n",
              "\n",
              "   potential                  team  \n",
              "2         92  Paris Saint-Germain   \n",
              "3         92            Liverpool   \n",
              "4         93      Atlético Madrid   \n",
              "5         91      Manchester City   \n",
              "7         91          Real Madrid   "
            ]
          },
          "execution_count": 60,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "age2630_df.head(5)"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "Lu5469leFtSi"
      },
      "source": [
        "From the above dataframe we can observe that in the age group 21 to 25, 'Kylian Mbappé' is ranked 1st, followed by 'Raheem Sterling' and 'Bernardo Silva'."
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "A04_GWx1FtSj"
      },
      "source": [
        "###### Age Group 31 to 35."
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "OMuB_cPEFtSj",
        "outputId": "2bd9e98b-5250-4362-b646-c8626bd4822b"
      },
      "outputs": [
        {
          "data": {
            "text/html": [
              "<div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>player_id</th>\n",
              "      <th>name</th>\n",
              "      <th>nationality</th>\n",
              "      <th>position</th>\n",
              "      <th>overall</th>\n",
              "      <th>age</th>\n",
              "      <th>hits</th>\n",
              "      <th>potential</th>\n",
              "      <th>team</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>0</th>\n",
              "      <td>158023</td>\n",
              "      <td>Lionel Messi</td>\n",
              "      <td>Argentina</td>\n",
              "      <td>ST|CF|RW</td>\n",
              "      <td>94</td>\n",
              "      <td>33</td>\n",
              "      <td>299</td>\n",
              "      <td>94</td>\n",
              "      <td>FC Barcelona</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>1</th>\n",
              "      <td>20801</td>\n",
              "      <td>Cristiano Ronaldo</td>\n",
              "      <td>Portugal</td>\n",
              "      <td>ST|LW</td>\n",
              "      <td>93</td>\n",
              "      <td>35</td>\n",
              "      <td>276</td>\n",
              "      <td>93</td>\n",
              "      <td>Juventus</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>6</th>\n",
              "      <td>188545</td>\n",
              "      <td>Robert Lewandowski</td>\n",
              "      <td>Poland</td>\n",
              "      <td>ST</td>\n",
              "      <td>91</td>\n",
              "      <td>31</td>\n",
              "      <td>89</td>\n",
              "      <td>91</td>\n",
              "      <td>FC Bayern München</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>12</th>\n",
              "      <td>153079</td>\n",
              "      <td>Sergio Agüero</td>\n",
              "      <td>Argentina</td>\n",
              "      <td>ST</td>\n",
              "      <td>90</td>\n",
              "      <td>32</td>\n",
              "      <td>50</td>\n",
              "      <td>90</td>\n",
              "      <td>Manchester City</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>18</th>\n",
              "      <td>177003</td>\n",
              "      <td>Luka Modric</td>\n",
              "      <td>Croatia</td>\n",
              "      <td>CM</td>\n",
              "      <td>89</td>\n",
              "      <td>34</td>\n",
              "      <td>31</td>\n",
              "      <td>89</td>\n",
              "      <td>Real Madrid</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>"
            ],
            "text/plain": [
              "    player_id                name nationality  position  overall  age  hits  \\\n",
              "0      158023        Lionel Messi   Argentina  ST|CF|RW       94   33   299   \n",
              "1       20801   Cristiano Ronaldo    Portugal     ST|LW       93   35   276   \n",
              "6      188545  Robert Lewandowski      Poland        ST       91   31    89   \n",
              "12     153079       Sergio Agüero   Argentina        ST       90   32    50   \n",
              "18     177003         Luka Modric     Croatia        CM       89   34    31   \n",
              "\n",
              "    potential                team  \n",
              "0          94       FC Barcelona   \n",
              "1          93           Juventus   \n",
              "6          91  FC Bayern München   \n",
              "12         90    Manchester City   \n",
              "18         89        Real Madrid   "
            ]
          },
          "execution_count": 61,
          "metadata": {},
          "output_type": "execute_result"
        }
      ],
      "source": [
        "age3135_df.head(5)"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "13s5SCo3FtSo"
      },
      "source": [
        "From the above dataframe we can observe that in the age group 21 to 25, 'Kylian Mbappé' is ranked 1st, followed by 'Raheem Sterling' and 'Bernardo Silva'."
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "gGOC4qtAFtSp"
      },
      "source": [
        "### Q: What are the ages in which maximum players are present?"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "KXe3kUwXFtSp"
      },
      "source": [
        "Let's see how many players are there in each of the different age. For finding this we will use a count plot."
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "sYKMutPmFtSq",
        "outputId": "3a64d256-581c-43eb-b8bb-46bf3d95b1b2"
      },
      "outputs": [
        {
          "data": {
            "image/png": "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\n",
            "text/plain": [
              "<Figure size 864x720 with 1 Axes>"
            ]
          },
          "metadata": {
            "needs_background": "light"
          },
          "output_type": "display_data"
        }
      ],
      "source": [
        "plt.figure(figsize=(12, 10))\n",
        "sns.countplot(x=dataraw_df.age)\n",
        "plt.xticks(rotation=90);"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "GTDNdST8FtSu"
      },
      "source": [
        "From the above graph we can conclude that there is maximum players of the age 24 followed by ages 23, 28 and 26. There are more than 1400 players of 24 years of age."
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "b0MhGAvbFtSv"
      },
      "outputs": [],
      "source": [
        "import jovian"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "R6pKUh-9FtSy",
        "outputId": "c985caf5-97a0-4572-a5de-c00aed290c4a"
      },
      "outputs": [
        {
          "data": {
            "application/javascript": [
              "window.require && require([\"base/js/namespace\"],function(Jupyter){Jupyter.notebook.save_checkpoint()})"
            ],
            "text/plain": [
              "<IPython.core.display.Javascript object>"
            ]
          },
          "metadata": {},
          "output_type": "display_data"
        },
        {
          "name": "stdout",
          "output_type": "stream",
          "text": [
            "[jovian] Attempting to save notebook..\r\n"
          ]
        }
      ],
      "source": [
        "jovian.commit()"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "Jdv1hTFTFtS0"
      },
      "source": [
        "## Inferences and Conclusion\n"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "zmVgs18kFtS0"
      },
      "source": [
        "We've drawn many interesting conclusions from this dataset and analysis. Some of them are - \n",
        "\n",
        "* There are 17981 players in Fifa 21.\n",
        "* There are 162 different countries from where there are players in Fifa 21. Out of which there are 3 countries with more than 1000 players.\n",
        "* There are 1496 players from England, 1138 players from Germany and 1055 players from Spain.\n",
        "* There are around 713 clubs with each club having around 30 players.\n",
        "* Maximum number of players falls in the age group 25 to 30.\n",
        "* More than 1400 players are of the age 24.\n",
        "* Highest overall rating in Fifa 21 is 94. Lionel Messi is the highest rated player with 94 overall rating."
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "77ilqBk1FtS0"
      },
      "outputs": [],
      "source": [
        "import jovian"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "37gYblnvFtS3"
      },
      "outputs": [],
      "source": [
        "jovian.commit(project='fifa_21_players_data_analysis_in_python1')"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "sJZCGaZDFtS6"
      },
      "source": [
        "## References and Future Work\n"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "syLn04EaFtS7"
      },
      "source": [
        "From this dataset of Fifa 21 we can further do many researches and analysis.Here are some ideas for further exploration:\n",
        "\n",
        "*  We can analyze more on the countries having the maximum players. As to what is the favourite sports in that country. The population of the country. The sporting infrastructure and facilities that favours football. The history of the country with football.\n",
        "* We can find out the teams which have the most players having overall rating of more than 90, more than 80 and so on. We can find out how many players with more than 90 rating are there in the top teams of the world like Real Madrid, Barcelona, Juventus, PSG, Man United, Man City, etc.\n",
        "* We can also analyze the data of top players individually. Like we can analyze the data of Lionel Messi and Cristiano Ronaldo to understand why they are rated so much higher than the others. We can find out there achievements and records, which can help us understand why they are so highly rated. Although for that purpose we will require different dataset with data of that individual player.\n",
        "\n",
        "\n",
        "References:\n",
        "\n",
        "* Pandas user guide: https://pandas.pydata.org/docs/user_guide/index.html\n",
        "* Matplotlib user guide: https://matplotlib.org/3.3.1/users/index.html\n",
        "* Seaborn user guide & tutorial: https://seaborn.pydata.org/tutorial.html"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "lcXm97R2FtS7"
      },
      "outputs": [],
      "source": [
        "import jovian"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "4F1qGBAKFtS9"
      },
      "outputs": [],
      "source": [
        "jovian.commit(project='fifa_21_players_data_analysis_in_python1')"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "Gc1wwFvZIy3-"
      },
      "outputs": [],
      "source": [
        ""
      ]
    }
  ],
  "metadata": {
    "colab": {
      "name": "fifa-21-players-data-analysis.ipynb",
      "provenance": []
    },
    "language_info": {
      "codemirror_mode": {
        "name": "ipython",
        "version": 3
      },
      "file_extension": ".py",
      "mimetype": "text/x-python",
      "name": "python",
      "nbconvert_exporter": "python",
      "pygments_lexer": "ipython3",
      "version": "3.8.3"
    }
  },
  "nbformat": 4,
  "nbformat_minor": 0
}
