function varargout = compressibilitycalculator(varargin)
% COMPRESSIBILITYCALCULATOR MATLAB code for compressibilitycalculator.fig
%      COMPRESSIBILITYCALCULATOR, by itself, creates a new COMPRESSIBILITYCALCULATOR or raises the existing
%      singleton*.
%
%      H = COMPRESSIBILITYCALCULATOR returns the handle to a new COMPRESSIBILITYCALCULATOR or the handle to
%      the existing singleton*.
%
%      COMPRESSIBILITYCALCULATOR('CALLBACK',hObject,eventData,handles,...) calls the local
%      function named CALLBACK in COMPRESSIBILITYCALCULATOR.M with the given input arguments.
%
%      COMPRESSIBILITYCALCULATOR('Property','Value',...) creates a new COMPRESSIBILITYCALCULATOR or raises
%      the existing singleton*.  Starting from the left, property value pairs are
%      applied to the GUI before compressibilitycalculator_OpeningFcn gets called.  An
%      unrecognized property name or invalid value makes property application
%      stop.  All inputs are passed to compressibilitycalculator_OpeningFcn via varargin.
%
%      *See GUI Options on GUIDE's Tools menu.  Choose "GUI allows only one
%      instance to run (singleton)".
%
% See also: GUIDE, GUIDATA, GUIHANDLES

% Edit the above text to modify the response to help compressibilitycalculator

% Last Modified by GUIDE v2.5 24-Apr-2017 15:34:37

% Begin initialization code - DO NOT EDIT
gui_Singleton = 1;
gui_State = struct('gui_Name',       mfilename, ...
                   'gui_Singleton',  gui_Singleton, ...
                   'gui_OpeningFcn', @compressibilitycalculator_OpeningFcn, ...
                   'gui_OutputFcn',  @compressibilitycalculator_OutputFcn, ...
                   'gui_LayoutFcn',  [] , ...
                   'gui_Callback',   []);
if nargin && ischar(varargin{1})
    gui_State.gui_Callback = str2func(varargin{1});
end

if nargout
    [varargout{1:nargout}] = gui_mainfcn(gui_State, varargin{:});
else
    gui_mainfcn(gui_State, varargin{:});
end
% End initialization code - DO NOT EDIT
end
% --- Executes just before compressibilitycalculator is made visible.
function compressibilitycalculator_OpeningFcn(hObject, eventdata, handles, varargin)
% This function has no output args, see OutputFcn.
% hObject    handle to figure
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)
% varargin   command line arguments to compressibilitycalculator (see VARARGIN)

% Choose default command line output for compressibilitycalculator
uiwait(msgbox(sprintf(['Please input air name (no case sensitivity)\n'...
    'Input Temperature and Pressure and choose the units they are in\n'...
    'Separate multiple entries by commas, no brackets needed, in order of matching conditions from left to right'])...
    ,'Instructions','modal'));

handles.output = hObject;

% Update handles structure
guidata(hObject, handles);

initialize_gui(hObject, handles, false);

%UIWAIT makes compressibilitycalculator wait for user response (see UIRESUME)
%uiwait(handles.figure1);
end
% --- Outputs from this function are returned to the command line.
function varargout = compressibilitycalculator_OutputFcn(hObject, eventdata, handles)
% varargout  cell array for returning output args (see VARARGOUT);
% hObject    handle to figure
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

% Get default command line output from handles structure
varargout{1} = handles.output;
end

% --- Executes during object creation, after setting all properties.
function temperature_CreateFcn(hObject, eventdata, handles)
% hObject    handle to temperature (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    empty - handles not created until after all CreateFcns called

% Hint: popupmenu controls usually have a white background on Windows.
%       See ISPC and COMPUTER.
if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end

end

function temperature_Callback(hObject, eventdata, handles)
% hObject    handle to temperature (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

% Hints: get(hObject,'String') returns contents of temperature as text
%        str2double(get(hObject,'String')) returns contents of temperature as a double
temperature = str2num(get(hObject, 'String'));
if isnan(temperature)
    set(hObject, 'String', 0);
    errordlg('Input must be a number','Error');
end

% Save the new temperature value
handles.eosdata.temperature= temperature;
guidata(hObject,handles)
end
% --- Executes during object creation, after setting all properties.
function pressure_CreateFcn(hObject, eventdata, handles)
% hObject    handle to pressure (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    empty - handles not created until after all CreateFcns called

% Hint: popupmenu controls usually have a white background on Windows.
%       See ISPC and COMPUTER.
if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end
end


function pressure_Callback(hObject, eventdata, handles)
% hObject    handle to pressure (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

% Hints: get(hObject,'String') returns contents of pressure as text
%        str2double(get(hObject,'String')) returns contents of pressure as a double
pressure = str2num(get(hObject, 'String'));
if isnan(pressure)
    set(hObject, 'String', 0);
    errordlg('Input must be a number','Error');
end

% Save the new pressure value
handles.eosdata.pressure = pressure;
guidata(hObject,handles)
end

% --- Executes on button press in calculate.
function calculate_Callback(hObject, eventdata, handles)
% hObject    handle to calculate (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)
s1= get(handles.gas,'String');
s2 = {'null'};
s3 = {''};
if strcmpi(s1,s2) == 1 || strcmpi(s1,s3) == 1
    errordlg('Please input gas type');
end
popup_sel_indextemp = get(handles.temperaturetype, 'Value');
popup_sel_indexpress = get(handles.pressuretype, 'Value');
if popup_sel_indextemp == 1
    
        tempkelvin= str2num(get(handles.temperature,'String'));
        tempsolve = tempkelvin;
        %Kelvin
end
if popup_sel_indextemp == 2
        tempcelsius= str2num(get(handles.temperature,'String'))+273.15;
        tempsolve = tempcelsius;
        %Celsius
end
if popup_sel_indextemp == 3
        tempfar= (str2num(get(handles.temperature,'String'))+459.67)*(5/9);
        tempsolve = tempfar;
        %Farenheit
end
if popup_sel_indextemp == 4
        tempran= str2num(get(handles.temperature,'String'))*(5/9);
        tempsolve = tempran;
        %Rankine
end
if popup_sel_indexpress == 1
        presspas= (str2num(get(handles.pressure,'String')))*1E-5;
        presssolve=presspas;
        %pascal
end
if popup_sel_indexpress == 2
        pressbar= str2num(get(handles.pressure,'String'));
        presssolve = pressbar;
        %bar
end
if popup_sel_indexpress == 3
        pressatm= (str2num(get(handles.pressure,'String')))*1.01325;
        presssolve = pressatm;
        %atm
end
if popup_sel_indexpress == 4
        presspsi= (str2num(get(handles.pressure,'String')))*0.0689475729;
        presssolve = presspsi;
        %psi
end
Zans=compressibility(get(handles.gas,'String'),tempsolve,presssolve);
set(handles.Zans, 'String', Zans);
uicontrol('Style','edit','Enable','off');
%Sets conditions for different inputs (such as constants and arrays) and
%creates plots of them with different colors and marks
T= sort(tempsolve);
P= sort(presssolve);
nt = length(T);
np = length(P);
if nt == 1 && np == 2
Pplot= linspace(P(1),P(end));
Z=compressibility(get(handles.gas,'String'),T,Pplot); 
axes(handles.axes1);
plot(Pplot,Z)
set(handles.Xlabel,'String','Pressure (Bar)');
set(handles.Ylabel,'String','Z');
title=['Z vs. ',get(handles.gas, 'String'),' at ',num2str(tempsolve),' Kelvin and ',num2str(Pplot(1)),' to ',num2str(Pplot(end)),' Pressure (bar)'];
set(handles.plottitle,'String', title);
end
if nt == 2 && np == 1
Tplot= linspace(T(1),T(end));
Z=compressibility(get(handles.gas,'String'),Tplot,P); 
axes(handles.axes1);
plot(Tplot,Z)
set(handles.Xlabel,'String','Temperature (Kelvin)');
set(handles.Ylabel,'String','Z');
title=['Z vs. ',get(handles.gas, 'String'),' from ', num2str(Tplot(1)),' to ',num2str(Tplot(end)),' Temperature (Kelvin)'];
set(handles.plottitle,'String', title);
end
if nt == 1 && np > 2
Pplot=linspace(P(1),P(end));
Z=compressibility(get(handles.gas,'String'),T,Pplot); 
axes(handles.axes1);
plot(Pplot,Z)
set(handles.Xlabel,'String','Pressure (Bar)');
set(handles.Ylabel,'String','Z');
title=['Z vs. ',get(handles.gas, 'String'),' at ',num2str(tempsolve),' Kelvin and ',num2str(Pplot(1)),' to ',num2str(Pplot(end)),' Pressure (bar)'];
set(handles.plottitle,'String', title);
end
if  np == 1 && nt > 2
Tplot=linspace(T(1),T(end));
Z=compressibility(get(handles.gas,'String'),Tplot,P); 
axes(handles.axes1);
plot(Tplot,Z)
set(handles.Xlabel,'String','Temperature (Kelvin)');
set(handles.Ylabel,'String','Z');
title=['Z vs. ',get(handles.gas, 'String'),' at ',num2str(Tplot(1)),' to ',num2str(Tplot(end)),' Kelvin and ',num2str(presssolve),' Pressure (bar)'];
set(handles.plottitle,'String', title);
end
if np == 1 && nt == 1
% Constant T
Pplot=linspace(P-10^(order(P)),P+10^(order(P)));
Z=compressibility(get(handles.gas,'String'),T,Pplot); 
axes(handles.axes1);
plot(Pplot,Z)
set(handles.Xlabel,'String','Pressure (bar)');
set(handles.Ylabel,'String','Z');
title=['Z vs. ',get(handles.gas, 'String'),' at ',num2str(tempsolve),' Kelvin and ',num2str(Pplot(1)),' to ',num2str(Pplot(end)),' Pressure (bar)'];
set(handles.plottitle,'String', title);
% Constant P
Tplot=linspace(T-10^(order(T)),T+10^(order(T)));
Z=compressibility(get(handles.gas,'String'),Tplot,P); 
axes(handles.axes1);
plot(Tplot,Z)
set(handles.Xlabel,'String','Temperature (Kelvin)');
set(handles.Ylabel,'String','Z');
set(handles.plotypepop, 'Value',1);
title=['Z vs. ',get(handles.gas, 'String'),' at ',num2str(Tplot(1)),' to ',num2str(Tplot(end)),' Kelvin and ',num2str(presssolve),' Pressure (bar)'];
set(handles.plottitle,'String', title);
end

if np > 1 && nt > 1
set(handles.plotypepop, 'Value',1);
     %Constant P
Tplot = linspace(T(1),T(end));
axes(handles.axes1);
plotStyle = {'--','-*','-r.','-s','-^'};
for i =1:np
Z=compressibility(get(handles.gas,'String'),Tplot,presssolve(i));
name{i} =['at ',num2str(presssolve(i)),' bar'];
h(i) = plot(Tplot,Z,plotStyle{i});
hold on
end
legend(h,name)
set(handles.Xlabel,'String','Temperature (Kelvin)');
set(handles.Ylabel,'String','Z');
hold off
title=['Z vs. ',get(handles.gas, 'String'),' at ',num2str(Tplot(1)),' to ',num2str(Tplot(end)),' Temperature (Kelvin)'];
set(handles.plottitle,'String', title);
end
end
% --- Executes on button press in reset.
function reset_Callback(hObject, eventdata, handles)
% hObject    handle to reset (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

initialize_gui(gcbf, handles, true);
end

% --------------------------------------------------------------------
function initialize_gui(fig_handle, handles, isreset)
% If the metricdata field is present and the reset flag is false, it means
% we are we are just re-initializing a GUI by calling it from the cmd line
% while it is up. So, bail out as we dont want to reset the data.
if isfield(handles, 'eosdata') && ~isreset
    return;
end
cla;
legend('hide')
handles.eosdata.temperature = 0;
handles.eosdata.pressure  = 0;
handles.eosdata.gas = 'null';
handles.eosdata.Zans = 0;
handles.eosdata.title = 'Title';
set(handles.temperature, 'String', handles.eosdata.temperature);
set(handles.pressure,  'String', handles.eosdata.pressure);
set(handles.gas, 'String',handles.eosdata.gas);
set(handles.Zans, 'String', handles.eosdata.Zans);
set(handles.plottitle, 'String',handles.eosdata.title);

% Update handles structure
guidata(handles.figure1, handles);
end

% --- Executes on selection change in temperaturetype.
function temperaturetype_Callback(hObject, eventdata, handles)
% hObject    handle to temperaturetype (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

% Hints: contents = cellstr(get(hObject,'String')) returns temperaturetype contents as cell array
%        contents{get(hObject,'Value')} returns selected item from temperaturetype

end

% --- Executes during object creation, after setting all properties.
function temperaturetype_CreateFcn(hObject, eventdata, handles)
% hObject    handle to temperaturetype (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    empty - handles not created until after all CreateFcns called

% Hint: popupmenu controls usually have a white background on Windows.
%       See ISPC and COMPUTER.
if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end
end

% --- Executes on selection change in pressuretype.
function pressuretype_Callback(hObject, eventdata, handles)
% hObject    handle to pressuretype (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

% Hints: contents = cellstr(get(hObject,'String')) returns pressuretype contents as cell array
%        contents{get(hObject,'Value')} returns selected item from pressuretype

end
% --- Executes during object creation, after setting all properties.
function pressuretype_CreateFcn(hObject, eventdata, handles)
% hObject    handle to pressuretype (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    empty - handles not created until after all CreateFcns called

% Hint: popupmenu controls usually have a white background on Windows.
%       See ISPC and COMPUTER.
if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end
end



function gas_Callback(hObject, eventdata, handles)
% hObject    handle to gas (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

% Hints: get(hObject,'String') returns contents of gas as text
%        str2double(get(hObject,'String')) returns contents of gas as a double
end
% --- Executes during object creation, after setting all properties.
function gas_CreateFcn(hObject, eventdata, handles)
% hObject    handle to gas (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    empty - handles not created until after all CreateFcns called

% Hint: edit controls usually have a white background on Windows.
%       See ISPC and COMPUTER.
if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end
end


% --- Executes on selection change in plotypepop.
function plotypepop_Callback(hObject, eventdata, handles)
% hObject    handle to plotypepop (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

% Hints: contents = cellstr(get(hObject,'String')) returns plotypepop contents as cell array
%        contents{get(hObject,'Value')} returns selected item from plotypepop
popup_sel_indextemp = get(handles.temperaturetype, 'Value');
popup_sel_indexpress = get(handles.pressuretype, 'Value');
if popup_sel_indextemp == 1
    
        tempkelvin= str2num(get(handles.temperature,'String'));
        tempsolve = tempkelvin;
        %Kelvin
end
if popup_sel_indextemp == 2
        tempcelsius= str2num(get(handles.temperature,'String'))+273.15;
        tempsolve = tempcelsius;
        %Celsius
end
if popup_sel_indextemp == 3
        tempfar= (str2num(get(handles.temperature,'String'))+459.67)*(5/9);
        tempsolve = tempfar;
        %Farenheit
end
if popup_sel_indextemp == 4
        tempran= str2num(get(handles.temperature,'String'))*(5/9);
        tempsolve = tempran;
        %Rankine
end
if popup_sel_indexpress == 1
        presspas= (str2num(get(handles.pressure,'String')))*1E-5;
        presssolve=presspas;
        %pascal
end
if popup_sel_indexpress == 2
        pressbar= str2num(get(handles.pressure,'String'));
        presssolve = pressbar;
        %bar
end
if popup_sel_indexpress == 3
        pressatm= (str2num(get(handles.pressure,'String')))*1.01325;
        presssolve = pressatm;
        %atm
end
if popup_sel_indexpress == 4
        presspsi= (str2num(get(handles.pressure,'String')))*0.0689475729;
        presssolve = presspsi;
        %psi
end
axes(handles.axes1);
cla;
T= sort(tempsolve);
P= sort(presssolve);
nt = length(T);
np = length(P);
popup_sel_indexplotype = get(handles.plotypepop, 'Value');
switch popup_sel_indexplotype
    case 1
        %Z vs. T constant P
 if nt > 1 && np >1
     %Constant P
Tplot = linspace(T(1),T(end));
axes(handles.axes1);
plotStyle = {'--','-*','-r.','-s','-^'};
for i =1:np
Z=compressibility(get(handles.gas,'String'),Tplot,presssolve(i));
name{i} =['at ',num2str(presssolve(i)),' bar'];
h(i) = plot(Tplot,Z,plotStyle{i});
hold on
end
legend(h,name)
set(handles.Xlabel,'String','Temperature (Kelvin)');
set(handles.Ylabel,'String','Z');
hold off
title=['Z vs. ',get(handles.gas, 'String'),' at ',num2str(Tplot(1)),' to ',num2str(Tplot(end)),' Temperature (Kelvin)'];
set(handles.plottitle,'String', title);
 end

if nt == 2 && np == 1
Tplot= linspace(T(1),T(end));
Z=compressibility(get(handles.gas,'String'),Tplot,P); 
axes(handles.axes1);
plot(Tplot,Z)
set(handles.Xlabel,'String','Temperature (Kelvin)');
set(handles.Ylabel,'String','Z');
title=['Z vs. ',get(handles.gas, 'String'),' from ',num2str(Tplot(1)),' to ',num2str(Tplot(end)),' Temperature (Kelvin) at ',num2str(presssolve),' Pressure (bar)'];
set(handles.plottitle,'String', title);
end
if  np == 1 && nt > 2
Tplot=linspace(T(1),T(end));
Z=compressibility(get(handles.gas,'String'),Tplot,P); 
axes(handles.axes1);
plot(Tplot,Z)
set(handles.Xlabel,'String','Temperature (Kelvin)');
set(handles.Ylabel,'String','Z');
title=['Z vs. ',get(handles.gas, 'String'),' at ',num2str(Tplot(1)),' to ',num2str(Tplot(end)),' Kelvin and ',num2str(presssolve),' Pressure (bar)'];
set(handles.plottitle,'String', title);
end
if np == 1 && nt == 1
% Constant P
Tplot=linspace(T-10^(order(T)),T+10^(order(T)));
Z=compressibility(get(handles.gas,'String'),Tplot,P); 
axes(handles.axes1);
plot(Tplot,Z)
set(handles.Xlabel,'String','Temperature (Kelvin)');
set(handles.Ylabel,'String','Z');
title=['Z vs. ',get(handles.gas, 'String'),' at ',num2str(Tplot(1)),' to ',num2str(Tplot(end)),' Kelvin and ',num2str(presssolve),' Pressure (bar)'];
set(handles.plottitle,'String', title);
end
if nt == 1 && np == 2
Tplot = linspace(T(1)-10^(order(T)),T(end)+10^(order(T)));
axes(handles.axes1);
plotStyle = {'--','-*','-r.','-s','-^'};
for i =1:np
Z=compressibility(get(handles.gas,'String'),Tplot,presssolve(i));
name{i} =['at ',num2str(presssolve(i)),' bar'];
h(i) = plot(Tplot,Z,plotStyle{i});
hold on
end
legend(h,name)
set(handles.Xlabel,'String','Temperature (Kelvin)');
set(handles.Ylabel,'String','Z');
hold off
title=['Z vs. ',get(handles.gas, 'String'),' at ',num2str(Tplot(1)),' to ',num2str(Tplot(end)),' Temperature (Kelvin) ' ];
set(handles.plottitle,'String', title);
end
if nt == 1 && np > 2
Tplot = linspace(T(1)-10^(order(T)),T(end)+10^(order(T)));
axes(handles.axes1);
plotStyle = {'--','-*','-r.','-s','-^'};
for i =1:np
Z=compressibility(get(handles.gas,'String'),Tplot,presssolve(i));
name{i} =['at ',num2str(presssolve(i)),' bar'];
h(i) = plot(Tplot,Z,plotStyle{i});
hold on
end
legend(h,name)
set(handles.Xlabel,'String','Temperature (Kelvin)');
set(handles.Ylabel,'String','Z');
hold off
title=['Z vs. ',get(handles.gas, 'String'),' at ',num2str(Tplot(1)),' to ',num2str(Tplot(end)),' Temperature (Kelvin) ' ];
set(handles.plottitle,'String', title);
end

    case 2
        %Z vs. P constant T
        if nt == 1 && np == 2
Pplot= linspace(P(1),P(end));
Z=compressibility(get(handles.gas,'String'),T,Pplot); 
axes(handles.axes1);
plot(Pplot,Z)
set(handles.Xlabel,'String','Pressure (Bar)');
set(handles.Ylabel,'String','Z');
title=['Z vs. ',get(handles.gas, 'String'),' at ',num2str(tempsolve),' Kelvin and ',num2str(Pplot(1)),' to ',num2str(Pplot(end)),' Pressure (bar)'];
set(handles.plottitle,'String', title);
        end
if nt == 1 && np > 2
Pplot=linspace(P(1),P(end));
Z=compressibility(get(handles.gas,'String'),T,Pplot); 
axes(handles.axes1);
plot(Pplot,Z)
set(handles.Xlabel,'String','Pressure (Bar)');
set(handles.Ylabel,'String','Z');
title=['Z vs. ',get(handles.gas, 'String'),' at ',num2str(tempsolve),' Kelvin and ',num2str(Pplot(1)),' to ',num2str(Pplot(end)),' Pressure (bar)'];
set(handles.plottitle,'String', title);
end
if np == 1 && nt == 1
% Constant T
Pplot=linspace(P-10^(order(P)),P+10^(order(P)));
Z=compressibility(get(handles.gas,'String'),T,Pplot); 
axes(handles.axes1);
plot(Pplot,Z)
set(handles.Xlabel,'String','Pressure (bar)');
set(handles.Ylabel,'String','Z');
title=['Z vs. ', get(handles.gas, 'String'),' at ',num2str(tempsolve),' Kelvin and ',num2str(Pplot(1)),' to ',num2str(Pplot(end)),' Pressure (bar)'];
set(handles.plottitle,'String', title);
end
if nt > 1 && np > 1
    %Constant T
Pplot = linspace(P(1),P(end));
axes(handles.axes1);
plotStyle = {'--','-*','-r.','-s','-^'};
for i =1:nt
Z=compressibility(get(handles.gas,'String'),tempsolve(i),Pplot); 
name{i}=['at ',num2str(tempsolve(i)),' Kelvin'];
h(i) = plot(Pplot,Z,plotStyle{i});
hold on
end
legend(h,name)
set(handles.Xlabel,'String','Pressure (bar)');
set(handles.Ylabel,'String','Z');
hold off
title=['Z vs. ',get(handles.gas, 'String'),' at ',num2str(Pplot(1)),' to ',num2str(Pplot(end)),' Pressure (bar)'];
set(handles.plottitle,'String', title);
end
if nt == 2 && np == 1
Pplot=linspace(P-10^(order(P)),P+10^(order(P)));
axes(handles.axes1);
plotStyle = {'--','-*','-r.','-s','-^'};
for i =1:nt
Z=compressibility(get(handles.gas,'String'),tempsolve(i),Pplot); 
name{i}=['at ',num2str(tempsolve(i)),' Kelvin'];
h(i) = plot(Pplot,Z,plotStyle{i});
hold on
end
legend(h,name)
set(handles.Xlabel,'String','Pressure (bar)');
set(handles.Ylabel,'String','Z');
hold off
title=['Z vs. ',get(handles.gas, 'String'),' from ', num2str(Pplot(1)),' to ',num2str(Pplot(end)),' Pressure (bar)'];
set(handles.plottitle,'String', title);
end
if  np == 1 && nt > 2
Pplot=linspace(P-10^(order(P)),P+10^(order(P)));
axes(handles.axes1);
plotStyle = {'--','-*','-r.','-s','-^'};
for i =1:nt
Z=compressibility(get(handles.gas,'String'),tempsolve(i),Pplot); 
name{i}=['at ',num2str(tempsolve(i)),' Kelvin'];
h(i) = plot(Pplot,Z,plotStyle{i});
hold on
end
legend(h,name)
set(handles.Xlabel,'String','Pressure (bar)');
set(handles.Ylabel,'String','Z');
hold off
title=['Z vs. ',get(handles.gas, 'String'),' from ', num2str(Pplot(1)),' to ',num2str(Pplot(end)),' Pressure (bar)'];
set(handles.plottitle,'String', title);
end

end
end
% --- Executes during object creation, after setting all properties.
function plotypepop_CreateFcn(hObject, eventdata, handles)
% hObject    handle to plotypepop (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    empty - handles not created until after all CreateFcns called

% Hint: popupmenu controls usually have a white background on Windows.
%       See ISPC and COMPUTER.
if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end
end
function figure1_SizeChangedFcn (hObject, eventdata, handles)
end
