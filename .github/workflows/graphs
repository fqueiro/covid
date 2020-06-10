import matplotlib.pyplot as plt
import seaborn as sns
from scipy.ndimage.filters import gaussian_filter1d

casos_wide = pd.read_csv('data_concelhos.csv')

casos_wide.columns = map(str.title, casos_wide.columns)
plot_days = 1000
smoothing = 7
concelhos_lx = {'name':'Lisboa','conc':['Lisboa','Loures','Odivelas','Sintra','Amadora','Cascais','Mafra','Oeiras','Vila Franca De Xira','Azambuja']}
concelhos_aml = {'name':'AML','conc':['Lisboa','Loures','Odivelas','Sintra','Amadora','Cascais','Mafra','Oeiras','Vila Franca De Xira','Azambuja','Alcochete', \
                'Almada','Barreiro','Moita','Montijo','Palmela','Setúbal','Sesimbra','Seixal']}
concelhos_lxsul = {'name':'LxSul','conc':['Sesimbra','Seixal','Barreiro','Montijo']}
concelhos_curia = {'name':'Curia','conc':['Anadia','Mealhada','Águeda']}
concelhos_amp = {'name':'AMP','conc':['Arouca','Espinho','Gondomar','Maia','Matosinhos','Oliveira De Azeméis','Paredes','Porto', \
                   'Póvoa De Varzim','Santa Maria Da Feira','Santo Tirso','São João Da Madeira','Trofa','Vale De Cambra', \
                   'Valongo','Vila Do Conde','Vila Nova De Gaia']}
round(len(list(casos_wide['Data'].tail(plot_days)))/10,0)
plticks = list(casos_wide['Data'].tail(plot_days))[10::max(1,int(len(list(casos_wide['Data'].tail(plot_days)))/20))]

def plot_conc(concelhos):
    fig, ax = plt.subplots(figsize=(15,12))
    for concelho in concelhos['conc']:
        casos_wide['temp'] = gaussian_filter1d(casos_wide[concelho].diff(), sigma=3)
        #_ = plt.plot(casos_wide['Data'].tail(plot_days), casos_wide[concelho].diff().rolling(window=smoothing).mean().tail(plot_days))
        _ = plt.plot(casos_wide['Data'].tail(plot_days), casos_wide['temp'].tail(plot_days))
        _ = ax.legend(concelhos['conc'])
        plt.xticks(plticks)
        fig.autofmt_xdate()
    fig.savefig(concelhos['name'])
    plt.show()

plot_conc(concelhos_aml)
plot_conc(concelhos_curia)
plot_conc(concelhos_amp)

